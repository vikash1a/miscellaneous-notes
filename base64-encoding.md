Base64 encoding is used to encode binary data to ASCII string format. 
It is used to transmit binary data over text base protocol such as HTTP or email.

- Contains only A-Z, a-z, 0-9, +, / and = used for padding
- 2^6 = 64 character excluding =
```
Value:  0  -> 'A'   |   1  -> 'B'   | ... | 25  -> 'Z'
Value: 26  -> 'a'   |  27  -> 'b'   | ... | 51  -> 'z'
Value: 52  -> '0'   |  53  -> '1'   | ... | 61  -> '9'
Value: 62  -> '+'   |  63  -> '/'
```
## How it works
1. Treat the binary input as stream of bytes
2. Divide the input into group of 3 bytes (24 bits), 
if there are fewer than 3 it is padded with 0
3. Each 24 bit group is divide into 4 groups of 6 bits, 
Each 6 bits group is then mapped to a character in base64 alphabet

## Example
```
input - Man
M -> 01001101
a -> 01100001
n -> 01101110 

Conacting,
010011010110000101101110

Split into 6 bits,
010011 010110 000101 101110

Map to Base64 alphabet,
010011 -> T
010110 -> W
000101 -> F
101110 -> u

Output: TWFu
```

## Disadvantages
- Increases data size by approximately 33% due to encoding overhead.

## ASCII encoding
- Uses 7 bit to represent characters, 2^7 = 128 characters
- Control Characters - 0-31, 127
- Printable characters
  - space - 32
  - digits - 48-57
  - A-Z - 65-90
  - a-z - 97-122
  - Symbols 