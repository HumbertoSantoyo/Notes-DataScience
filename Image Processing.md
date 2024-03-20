# Introduction

## Load

Will use scikit-Image

`image_object = plt.imread(path)` to load the image into a ndarray

`np.shape(image_obj)` = (n_x, n_y, color_depth)

`image_object.size()` = number of pixels

`color.rgb2gray(image)`

`np.flipud(image_obj)`to vertically flip

`np.fliplr(image_obj)`to horizontally flip



*_To display histogram_*

```python
blue = image[:,:,2]

plt.hist(blue.ravel(), bins = 256)
plt.title('Blue Histogram')
plt.show()
```

