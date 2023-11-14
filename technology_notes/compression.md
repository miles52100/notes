# Compression

There are two categories

  1. Lossless: you can restore the original data stream without loss of information 
  2. Lossy: you tolerate some loss of information so the de-compressed data stream is not identical to the original. This is relevant to scenarios where prefect reconstruction is not necessary, e.g., image, audio, video etc.

## Lossless compression

There are three broad categories of techniques

  1. Statistical data compression
  2. Dictionary-based data compression
  3. Transform-based data compression

Received wisdom is that Statistical data compression is the best performing but is computation heavy.

The rough idea behind these compressions is as follows:

  * Statistical data compression: encode frequent letters in fewer bits than infrequent letters. Examples include WinZIP and 7-Zip.
  * Dictionary-based compression: substitute words with shorter references in a dictionary. Lempel-Ziv based algorithms are the most prominent examples.
  * Transform-based compression: somewhat different. A sequence of transforms, e.g., Burrows Wheeler Transform or Sort Transform followed by Move To Front Encoding. These map the input data into a representation that is easy to compress. Achieving the final compression is done with another lossless technique, typically a statistical compression.



---
---
## References

1. [On Statistical Data Compression - thesis](https://d-nb.info/1096221012/34#:~:text=A%20statistical%20data%20compressor%20processes%20an%20input%20text,distribution%20and%20the%20next%20letter%20into%20a%20codeword.)

 2. 