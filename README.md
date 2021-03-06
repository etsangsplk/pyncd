# Pyncd
A Python powered normalized compression distance (NCD) calculator.

All data are created equal but some data are more alike than others. The NCD uses a method expressing this alikeness
using a similarity metric based on compression. The NCD is a non-negative number 0 ≤ r ≤ 1 representing how different the two files are. Smaller numbers represent more similar files. It is parameter-free in that it doesn’t use any features or background knowledge about the data, and can without changes be applied to different areas and across area boundaries.

## Usage
```bash
$ git clone git@github.com:alephmelo/pyncd.git
$ cd pyncd
$ python pyncd.py <file1> <file2>
```

## Examples
Let's measure the nomalized compression distance between a square image and the same image.
``` python
x = open('examples/imgs/square.png', 'rb').read() # square image
y = open('examples/imgs/square.png', 'rb').read() # square image
```
```
$ python pyncd.py
0.02
```
As we can see, the ncd result was almost 0, so we can say that the two files are very much alike, even though they are the same image, this happens because some compression algorithm works better with some kind of files. 

Now, we are measuring the distance between a square image and a rectangle image.
``` python
x = open('examples/imgs/square.png', 'rb').read() # square image
y = open('examples/imgs/rectangle.png', 'rb').read() # rectangle image
```
```
$ python pyncd.py
0.53
```
We can see that the distance between the files are 53% alike.

And finnaly we are measuring the distance between a square image and a circle image.
``` python
x = open('examples/imgs/square.png', 'rb').read() # square image
y = open('examples/imgs/circle.png', 'rb').read() # circle image
```
```
$ python pyncd.py
0.80
```
The NCD between the files is 80% now. 

These are great stats considering that the NCD doesn't need to see inside the file. 
Think big picture!

## To-do
- [ ] Implement setup.py
- [x] Be like ```$ pyncd <file1> <file2>```
- [ ] Support directories and create distance matrix. 

#### References
* Rudi Cilibrasi and Paul M. B. Vitányi. Clustering by compression. *IEEE Transactions on Information Theory*, 51:1523–1545, 2005
