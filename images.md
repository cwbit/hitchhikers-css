# Image Tricks
A collection of tricks we constantly need to use and got sick of forgetting. Add yours with a PR!

1. [Centering an Image](#centering-an-image)
2. [Constrain Size](#constrain-size)

### Centering an Image
Apply the following style directly to the `<img>`

```
	margin-right: auto;
	margin-left: auto
```

or create the following css class and assign it to the `<img>`

```
.img-centered{
	margin-left: auto;
	margin-right: auto;
}
```

### Constrain Size
**if anyone knows a better way, please submit a PR. this requires manually setting a size, which is ... uhg-ly**

If you're able to get away with using a `background-image` your life will be easier, just use..

```
background-image: url(..your/image..);
background-size: [contain|cover]
```
Otherwise you need to determine what mode you want: width-restricted, or height-restricted. You can't have both.


```
.img-restricted-height{
	max-height: 200px; // change to your actual need
	width: auto;
}

// .. or ..

.img-restricted-width{
	max-width: 200px; // change to actual need
	height: auto;
}
```