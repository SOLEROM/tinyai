# KWSV3


![alt text](image-20.png)

![alt text](image-21.png)


* yaml out_offset is moving between 0x200 to 0x0 each layer to share the same space?

* we have input level of 128 - but only 64 processors on the max78;

# multipass processing:

![alt text](image-23.png)

round to the upper one!

![alt text](image-24.png)

### example for 165 inputs:

![alt text](image-25.png)

![alt text](image-26.png)

# back

![alt text](image.png)

input

![alt text](image-1.png)

## layer1

![alt text](image-3.png)

![alt text](image-2.png)

![alt text](image-22.png)

```
processors:

128/64= 2

128/2/4*4=64 =>>> 0xffff...fff => all on


```

## layer2

![alt text](image-4.png)

* the input will reduced by 1 at each side (128-2=126)


![alt text](image-5.png)

![alt text](image-27.png)

```
processors:
100/64 => 2
100/2*4*4 = 52

```

## layer3

![alt text](image-6.png)

![alt text](image-7.png)

![alt text](image-8.png)

pad to return to 64

![alt text](image-9.png)

![alt text](image-28.png)

```
processors:


```

## layer4

![alt text](image-10.png)

![alt text](image-29.png)

```
processors:
64 input - we can do all the work in one pass - all on

```

## layer5

![alt text](image-11.png)

![alt text](image-30.png)

```
processors:


```

## layer6

![alt text](image-12.png)

![alt text](image-31.png)

```
processors:


```

## layer7

![alt text](image-13.png)

![alt text](image-32.png)

```
processors:


```

## layer8

![alt text](image-14.png)

![alt text](image-15.png)

![alt text](image-16.png)

![alt text](image-33.png)

```
processors:


```


## layer9 - output

![alt text](image-19.png)

* fully connected is fletten true with operation = MLP = MultiLayer Preceptron;
* the output width will be 32 bit !!! 

![alt text](image-34.png)

 

```
processors:


```

# front

![alt text](image-17.png)

![alt text](image-18.png)

* prevent overfit