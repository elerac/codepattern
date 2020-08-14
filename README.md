# Structured Light
These programs generate and decode structured light. 

Currently supports 
* [Binary code](#Binary-code)
* [Gray code](#Gray-code)
* [XOR code](#XOR-code)
* [Ramp code](#Ramp-code)
* [Phase Shifting](#Phase-Shifting)
* [Single stripe](#Single-stripe)

## Requirement
* Numpy

## Installation
```sh
git clone https://github.com/elerac/structuredlight.git 
cd structuredlight
python setup.py install
```

## Usage
```python
import structuredlight as sl

width  = 640
height = 480

gray = sl.Gray()

imlist_pattern = gray.generate((width, height))

# Projecting patterns from a projector (or display) and capture images
imlist_captured = imlist_pattern

img_index = gray.decode(imlist_captured, thresh=127)

print(img_index)
# [[  0   1   2 ... 637 638 639]
#  [  0   1   2 ... 637 638 639]
#  ...
#  [  0   1   2 ... 637 638 639]]
```

## Supported structured light

### Binary code
![](documents/binary.gif)
```python
binary = sl.Binary()
imlist_pattern = binary.generate((width, height))
img_index    = binary.decode(imlist_pattern, thresh=127)
```

### Gray code
![](documents/gray.gif)
```python
gray = sl.Gray()
imlist_pattern = gray.generate((width, height))
img_index    = gray.decode(imlist_pattern, thresh=127)
```

### XOR code
![](documents/xor.gif)
```python
xor = sl.XOR(index_last=-1)
imlist_pattern = xor.generate((width, height))
img_index    = xor.decode(imlist_pattern, thresh=127)
```

### Ramp code
![](documents/ramp.gif)
```python
ramp = sl.Ramp()
imlist_pattern = ramp.generate((width, height))
img_index    = ramp.decode(imlist_pattern)
```

### Phase-Shifting
![](documents/phaseshifting.gif)
```python
phaseshifting = sl.PhaseShifting(num=3)
imlist_pattern = phaseshifting.generate((width, height))
img_index    = phaseshifting.decode(imlist_pattern)
```

### Single stripe
![](documents/stripe.gif)
```python
stripe = sl.Stripe()
imlist_pattern = stripe.generate((width, height))
img_index    = stripe.decode(imlist_pattern)
```

## Tips
### How to binarize a grayscale image
Some of the code (Binary, Gray, XOR, ...) needs to binarize. This program provides three methods. [See the wiki for details.](https://github.com/elerac/structuredlight/wiki#how-to-binarize-a-grayscale-image)

### How to display images in full screen
When you use structured light, you'll need a full screen display from a projector or display. [Here is a program to display the image in full screen.](https://github.com/elerac/fullscreen)