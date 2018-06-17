# Huffman Coding - Python Implementation
## Project Description
In this project, we will demonstrate how to compress and decompress a text file using Huffman coding. The project is divided into three main parts:

 1.  **Constructing Huffman code** ( [HuffmanCode.ipynb](https://github.com/ybruce61414/Data-Structures/blob/master/Tree/HuffmanCoding/HuffmanCode.ipynb)):
     * This part will show you how to build a **Huffman tree** from input characters, and generate Huffman codes by traversing the Huffman tree. 
 2.  **Encoding the file** ([main_encode.ipynb](https://github.com/ybruce61414/Data-Structures/blob/master/Tree/HuffmanCoding/main_encode.ipynb)):
      * This part will demonstrate how to encode the text into Huffman string, and save it as binary file in ASCII hex format. 
  
 3.  **Decoding the file** ([main_decode.ipynb](https://github.com/ybruce61414/Data-Structures/blob/master/Tree/HuffmanCoding/main_decode.ipynb)):
     * This part will demonstrate how to decode the binary file, and convert it into text data with Huffman code of each character.  
         

## What is Huffman coding?
Huffman coding is a lossless data compression algorithm. The idea is to assign variable-length codes to input characters, instead of fixed-length codes. Lengths of the assigned codes are based on the frequencies of corresponding characters. The most frequent character gets the smallest code, whereas the least frequent character gets the largest code.

Normally, each character in a text file is stored in eight bits using an encoding called ASCII. A Huffman-encoded file breaks down the rigid 8-bit structure so that the most commonly used characters are stored in just a few bits ('a' could be "10" or "1000" rather than the ASCII, which is "01100001").  However, the least common characters will take up more than 8 bits ('z' might be "00100011010") in some rare situations. Huffman encoding, on the whole, creates a much smaller file than the original one.

 ## How to generate Huffman code ?
 There are mainly two major parts in generating Huffman code:
 
1.  Build a Huffman tree from input characters.
2.  Traverse the Huffman tree and assign codes to characters.
 ![Alt Huffman tree](image/huffman_tree.png)
 
 **Step for building a Huffman tree**
 
 - Count the frequency of each character.  
   ```python
   {'A':10, 'B':5, 'C':7, 'D':15, 'E':20, 'F':45}
   ``` 
 -  Extract two nodes with the minimum frequencies.
 -  Create a **parent node** with a frequency that is the sum of the two extracted nodes' frequencies, and make the first extracted node as it's **left child** and the other as it's **right child**.
 - Do the above two steps successively until there is only one node which all others spring from, and which is the root of the tree.
 - The Huffman tree is complete.
 
 **Step for assigning codes from Huffman Tree**
 
 - Traverse the tree to reach each leaf node(character) from the root.
 - Append a **0** for each time you take the **left branch**, and a **1** for each time you take the **right branch**. Print the code word when a leaf node is encountered.
 - The Huffman code is obtained.
    ```python
   {'A':'000', 'B':'0010', 'C':'0011', 'D':'010', 'E':'011', 'F':'1'}
   ``` 
   
 ## Part 1: Constructing Huffman code
 Firstly, we let the basic element be the class `Huffman_node` to store the **input characters** and its corresponding **frequencies**, and define the `repr()` method to print out the status of the nodes. 
 
 ```python
 class Huffman_node():
    def __init__(self,cha,freq):
        self.cha = cha
        self.freq = freq
        self.Lchild = None
        self.Rchild = None
   
    def __repr__(self):
            return '(node object %s:%d)' % (self.cha,self.freq)
 ``` 
 Secondly we create the class `HuffmanCoding`  to generate the tree and Huffman code. The source code is as below:
 
 ```python
 class HuffmanCoding():
    def __init__(self,text):
        self.root = None
        self.text = text
        self.nodedic = {}
        self.huffcodes = {}
        self.encodes = []
        self.decodes = []
                
    #----------- generating huffman tree -----------   
    def generate_tree(self):
        self.generate_node() 
        while len(self.nodedic) != 1:
            min_node1 = self.find_minNode()
            min_node2 = self.find_minNode()
            self.root = self.merge_nodes(min_node1,min_node2)
        return self.root              
        
    #---- function set for generating huffman tree -----
    def character_freq(self):
        #generate dic-{cha:freq}
        count = {}
        for cha in self.text:
            count.setdefault(cha,0)
            count[cha] += 1
        return count     

    def generate_node(self):
        #generate dic-{freq:node}
        c = self.character_freq()
        #storing each cha & freq into huffmanNode
        for k,v in c.items():
            newnode = Huffman_node(k,v)
            #multiple value for the same key
            #dic-{key:[ob1,ob2..]}
            self.nodedic.setdefault(v,[]).append(newnode)
        return self.nodedic
    
    def find_minNode(self):
        keys = list(self.nodedic.keys())
        minkey, minlist = keys[0], self.nodedic[keys[0]]
        for k,v in self.nodedic.items():
            if minkey > k:
                minkey,minlist = k,v
        minvalue = minlist.pop(0)
        if not minlist:
            #empty list,delete the minNode from dic
            del self.nodedic[minkey]    
        #return minNode object
        return minvalue 
    
    def merge_nodes(self,min1,min2):
        newnode = Huffman_node(min1.cha + min2.cha,min1.freq + min2.freq)
        newnode.Lchild,newnode.Rchild = min1,min2
        #adding newnode into self.nodedic
        self.nodedic.setdefault(min1.freq + min2.freq,[]).append(newnode) 
        return newnode
    
    #----------generating huffman code-----------
    def generate_huffcode(self):
        code = ''
        if self.root != None:
            return self.rec_generate_huffcode(self.root,code)         
            
    def rec_generate_huffcode(self,cur_node,codestr):
        if not cur_node.Lchild and not cur_node.Rchild:
            self.huffcodes[cur_node.cha] = codestr  
        if cur_node.Lchild:
            self.rec_generate_huffcode(cur_node.Lchild,codestr + '0')
        if cur_node.Rchild:
            self.rec_generate_huffcode(cur_node.Rchild,codestr + '1')
         
    #-----------------compression-------------------
    def encode(self):
        for cha in self.text:
            self.encodes.append(self.huffcodes[cha])
        #strings in list merge into one string    
        self.encodes = ''.join(self.encodes)
        #turn encodes into string
        return self.encodes     
        
    #----------------decompression------------------
    def decode(self):
        temp_str,temp_dic = '',{}
        #reverse huffcodes
        for k,v in self.huffcodes.items():
            temp_dic[v] = k
        
        for binary_code in self.encodes:
            temp_str += binary_code
            if temp_str in temp_dic.keys():
                self.decodes.append(temp_dic[temp_str])
                temp_str = ''
        self.decodes = ''.join(self.decodes)         
        return self.decodes 
 ```        
 
 
 
 
 
 
 
 
 
 