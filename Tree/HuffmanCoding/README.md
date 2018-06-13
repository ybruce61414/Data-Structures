# Huffman Coding with Python
## Project Description
In this project, we will demonstrate how to compress and decompress a text file using Huffman coding.  

The project is divided into three main parts. One is constructing Huffman code,which is in [HuffmanCode.ipynb](https://github.com/ybruce61414/Data-Structures/blob/master/Tree/HuffmanCoding/HuffmanCode.ipynb), another is encoding the file, which is in [main_encode.ipynb](https://github.com/ybruce61414/Data-Structures/blob/master/Tree/HuffmanCoding/main_encode.ipynb), and the other is decoding the file, which is in [main_decode.ipynb](https://github.com/ybruce61414/Data-Structures/blob/master/Tree/HuffmanCoding/main_decode.ipynb).

## What is Huffman coding?
Huffman coding is a lossless data compression algorithm. The idea is to assign variable-length codes to input characters, instead of fixed-length codes. Lengths of the assigned codes are based on the frequencies of corresponding characters. The most frequent character gets the smallest code, and the least frequent character gets the largest code.

Normally, each character in a text file is stored as eight bits that map to that character using an encoding called ASCII. A Huffman-encoded file breaks down the rigid 8-bit structure so that the most commonly used characters are stored in just a few bits ('a' could be "10" or "1000" rather than the ASCII, which is "01100001").  However, the least common characters will take up more than 8 bits ('z' might be "00100011010") in some rare situations. Huffman encoding, on the whole, creates a much smaller file than the original one.