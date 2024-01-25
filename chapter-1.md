# Binary
Binary is just like counting in normal numbers like this. To count up in normal numbers you count from 0-9, 9 is the last number of each digit, once you reach 9 and u try to count up from nine again you would come back to 0 and you increment (count up) the left digit before it. The same rules apply to every digit, once it reaches 9+1 __(im saying nine plus one because u cant say 10 because that doesnt fit in a single digit)__ then it also increments the digit to the left of it. if there is no digit to the left of it u imagine an invisible 0 which u incrmement and make 1 and it becomes visible again.

For binary its just like that, but rather than 0-9 __(10 different numbers)__, its 0-1 __(2 different numbers)__. 

For the following ill make the invisible zeros visible, theres an infinite number of them but ill make the ones ill eventually use visible at all times.
**Counting Up Normally**
```
00
01
...234567...
08
09
10
11
...12-19...
20
```

  **Counting Up in Binary**
```
00
01
10
11
```

In the above list of binary numbers heres what i did: Each bullet points number to the left of it corrosponds to one of the 4 lines in the list of binary numbers. Also the line number is the value of the binary number. that list of binary numbers goes from 0-3, so 4 different numbers.

1. We wont increment the first one since we need to start off with 00 at some point.
2. The right most digit is currently 0 so we increment it
3. The right most digit is currently 1 so we try to incrmenet it but it just cycles back to 0, same way 9+1 cycles right back to 0 and the digit to the left counts up. so for binary, if we increment the right most 1, it becomes 0. since that overflow happened (where it comes back to 0 and we know it) we will look at the number to the left of it and count it up
4. Since we previously reset the right most number to 0, it means we can count again, so it goes to 1. 

**What are bits**
Those binary numbers are 2 bits, those 4 numbers in binary are all 4 possible combinations of 2 different 1s or 0s.

**What is binary for**
Its just a way of storing a number. The reason we dont store numbers from 0-9 instead is cause you cant easily. Computers used to work a similar way to 0-9 (aka decimal counting system) but the problem was they used voltages to use as a measure of what number is being sent. Second problem is storing a voltage accuratly isnt easy as overtime it can start to change its self. Binary numbers on the other hand are either ON or OFF, there is ***NO*** inbetween so even if data stored electrically were to slightly change or data sent over a wire were to slightly deform, it wouldnt cause an issue because it hasnt crossed the voltage limit to chane from a 1 to a 0.
**What is base-x**
X im using as a placeholder, in X's place should go a number. Binary is in base 2, your normal numbers are in base 10. If you see the patteren, binary has 2 different numbers that fit in a single digit, 0 and 1. Your normal numbers (which are decimal) can have 10 different numbers for a single digit, 0, 1, 2, 3, 4, 5, 6, 7, 8 and 9.

There are different ways to store information on a computer, but if you want to store data it at the lowest HAS to be binary, and only can be (if it was generated on a computer). Computers store base 2 more efficiently because thats what its transsitors store for memory and transmit throughout. They can store base-10 as text, but that is inefficient because computers dont store base-10 directly. to store a number like the following `9237871` the computer turns it into text then stores the binary of the text. ill explain how text binary works later.
**End**
Just one note to retouch, binary and all the base-x's are simply and ONLY a way to store a number, 2 bit number go up to 3, 3 bit numbers go up to 7, 4 bit numbers go up to 15. 

**Equasions**
To calculate the largest number a binary number stores based on the number of bits u have. 
```matlab
f(bits) -> (2^bits)-1
// Word Form: (2 to the power of n) minus 1. N as in the number of bits.
```

To calculate the total number of possible combinations a binary number can have by flipping its 1s and 0s by the number of bits.
```matlab
f(bits) -> (2^bits)
// Word Form: 2 to the power of n. N as in the number of bits.
```
# Ram and using Binary
You might wonder, if computers simply work with binary, that means they work with numbers, but how do numbers store your messages and everything? Its all about encoding. The binary numbers SIMPLY serve as codes that translate to some meaning based on contxt.

Saying "car" makes no sense. But adding other words for content makes sense, "that is a car".

**Bit**
A bit is just a single digit of binary. Example: `0`

**Nibble**
4 bits. Example: `0101`

**Byte**
2 Nibbles: Example: `01001011`

**Internal**
Since your still learning english i added this. Something internal in the context of programming is something that isnt meant for you to see. Its something it uses to sustain its self usually, you shouldnt use.

**Storage of binary**
Also binary is stored in your computer as a huge list. its just a bunch of ones and zeros that keep going on and on and on in your harddrive or NVME or SSD even ram, what ever it is some form of storage.
```
01010101010010010111011111101010001011011111000010110101000011101010000101
// Random garage bits with no meaning yet
```

__How can we figure out how many numbers (NOT DIGITS) are in the list above list?__
Well you cant just by looking at that, you could interpet it alot of ways
- You could interpeet it all as one GIANT binary number with 74 bits.
- You could split it up every 4 bits. so ill bold every other number ive extracted from here, the unbolded is just like the bolded but i bolded to show the separation of the numbers, i could have used spaces too. **0101**0101**0100**1001**0111**0111**1110**1010**0010**1101**1111**0000**1011**0101**0000**1110**1010**0001**01**

__Architecture__
This is a set of rules for a CPU on how binary will be interpeted. This is the answer to the above problem. What architecture can do is define the number of bits each number can have. ever seen the word 64-bit or 32-bit. These both say that thats how many bits each number is. on 64 bit systems, a number is defined every 64 bits.
__Addresses__
Now me saying the whole thing is one whole big list of bits was actually wrong, but intentionally. While yes it is a common way for **sending** data through a wire __more on that later__, it has one problem. its that u cant find a specific bit, or byte, or any data easily. We need to find data to actually do something useful. otherwise this serves no purpose.

Now lets create a little custom architecture (set of rules). Our architecture is only 4 bits, so each binary number is 4 bits. Now one thing to note, it wont be 4 bits everywhere, 4 bits mainly reffers to how the little magical function box called ur CPU takes data, __more on how a cpu works later too__.

But for this example, the number of bits in our architecture reffers to how many bits data and ADDRESSES have in ram. Ram is simply a table with an address and value column. You could think of it as a neighbor hood ith the value column being resident owner.

Heres a simple depiction of ram i made
```
     RAM
Address | Value
0000    | 0000
0001    | 0000
0010    | 0000
0011    | 0000
```

By default every value in ram is binary `0000` which translates to 0 in our normal numbers. The addresses tho you can see actually count up from 0.

__How to use ram__
Its VERY easy, you can do 2 main commands, there are other internal commands used by the CPU for things the ram needs to stay working correctly but you wont use them.

1. SET: Set will set the value to something you want at a given address. You could set for example the data at `0000` to `1001`. 
2. GET: Getting will simply give you back the value that is stored at a given address in ram. If i were to do the set command example above this, then run GET from `0000` you would get `1001` because we set that.

# Storing Strings
Now were going to use alot of the newfound knowlege and use it to store **strings** aka text as you know it.
Now strings are just another form of encoding, same way binary is just a way to encode or turn decimal numbers into something electronics can store reliably, strings are a way to encode our letters and symbols for storing on a computer.

Now you might rmemeber how i said discord stores numbers in our messages as text but there just numbers, so how does that make sense? well ull see.

__Encoding__
Now strings firstly need a character encoding. this basicly says that x number represents this symbol.
so lets make a simple encoding architecture. this table will show what numbers represent what symbol. Now for the same of simplicity i wont write them as binary, but rmemeber, all numbers can be turned into binary, so the binary forms of the numbers on the left column is what ur computer stores this table as.

Remember, our architecture is 4 bits, so the number column translates to a 4 bit number.
```
Number | Symbol
0      | <SPACE>
1      | a
2      | b
3      | c
4      | d
5      | e
6      | f
// And so on so fourth, it even includes numbers, capital letters etc...
```

__Problem__
Heres the problem, the symbol im referencing doesnt exist in binary, in real computers the symbol is ALSO a number, but that number is an address in ram that indicates where its manager is. the manager basicly is responsible for calculating and drawing the pixels necesary for that letter or symbol. ull understand this whole pointing idea later when i explain CPUs, currently you dont know how binary can draw anything at all yet.

__Simple__
Since we are being simple for now as you dont have CPU knowlege yet, ive been using the letter its self for now, a, b, c, d, etc...

__Example__
To encode the word `abfe` for a computer. it would look like this. 1 2 6 5. I must show you the binary for this to show you the use of the architecture.
ABFE = **0001**0010**0110**0101

Since our architecture is 4 bits, we know exactly where each segments ends

**Mathematical Method of Binary to Decimal Conversion**
This method is VERY fast, it lets you convert binary to decimal (your numbers) really quickly.
Heres how it works, previously in the binary lesson I didnt add this for simplicity. Now I will.
currently the exacmple of **ABFE** as binary looks confusing. so lets disect it.

There are a few elements needed
- number of bits
- which side to start from
- how to convert

lets start with the nuber of bits, our architecture got that covered for us/
Next we need to decide which side to start from and we need to understand the math.

how this works is you pick starting from the right side. that means the least influencial bit is on the right, thats how it is in normal english numbers. writing 2048, 8 on the right if set to 0 or 9 has very little affect on the value, where as change the 2 on the left to a 3 has an effect magnitude of one thousand. making the left most infleuncial/signifigant and right least influencial/signifigant

now in binary the magnitude or amount a specific digit contributes is determined by its position with the power of 2. we use the power of 2 because u can have 2 numbers per digit for binary.

for 4 bits, with the least signifigant bit on the right, its magnitudes look like this
8 4 2 1
> you can see that the numbers double each time they go left

look the same thing happens with english numbers magintudes
1000 100 10 1

these are the place values
Now its only a matter of seeing if the number is a 1, checking its placevalue number and adding it all up for every number.

__Example__
Lets say we have the binary number `1011`

heres our placevalues or magnitudes `8 4 2 1`

now lets start on either side of the binary number and check the placevalue corrosponding to the position of the bit.
- starting from the right the first bit is 1, the placevalue magnitude is `1`
- next to the left is 1 again, this time the placevalue mag is `2`, lets remember that
- the next to the left this time is 0, so we ignore this
- the last one to the left most position is 1 again, the placevalue mag is `8`

now lets just add our numbers up, `1 + 2 + 8`. Another simpler way but less efficient is to multiply the placevalue mag * the bit. if the bit is 0 the anything multiplied by 0 is 0, so in the end you'd simply be adding 0. but the cost of mulltiplication still exists. it might be faster sometimes as it doesnt reuire a jump instruction in some senarios. youll learn about **instruction jumping** later.

Anyway, with this new placevalue knowlege of it applying to binary too you can now understand **ABFE** as binary which is `0001 0010 0110 0101`

**Limitation of ram**
While the number of bits used to represent the address of ram is the number of bits the architecture allows. the same cannot be said for the values. There is a very specific and very practical reason for this. Typical ram such as the one your using to read this text has each value to be 8 bits. **8 bits is a single byte**. To store strings, the string is typically split up. 

**ASCII**
ASCII stands for American Standard Code for Information Interchange, its very similar to our simple encoding we wrote for strings, aka text. ASCII is a standard owned by the US and simply uses different numbers to represent different symbols than our simple encoding.
ASCII is very limited, rmember how we can only have 1 byte per address in ram, well (2^8) will give us the number of symbols we can support, which is 256. 256 is not enough to cover many languages, and only covers english and some simple special characters. 
