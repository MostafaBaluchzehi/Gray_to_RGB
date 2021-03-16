## Transform Grayscale Images to RGB

Data pre-processing is critical for computer vision applications, and properly converting grayscale images to the RGB format expected by current deep learning frameworks is an essential technique.

### I use the following code to convert gray-scale images to RGB and I got a good result.


```
import os
from PIL import Image, ImageMath

data_dir = "data_dir/my_data"
rgb_data = "data_dir/my_rgb_data"
img_files = os.listdir(rgb_data)

for img in img_files:
    myimg = Image.open(data_dir + "/" + img)
    if myimg.mode != 'RGB':
        if myimg.mode == 'I':
            myimg = ImageMath.eval('im/256', {'im': img})
        myimg = myimg.convert('RGB')
        myimg.save(rgb_data + "/" + img)
```

### If you have a numpy array image, you can first convert it to PIL image

```
PIL_image = Image.fromarray(np.uint8(output)).convert('RGB')
```

