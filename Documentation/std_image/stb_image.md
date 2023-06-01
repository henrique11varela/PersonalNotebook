# stb_image

[Back](../Documentation.md)

[Github Repo for this lib](https://github.com/nothings/stb)  
[Youtube playlist tutorial](https://www.youtube.com/playlist?list=PLG5M8QIx5lkzdGkdYQeeCK__As6sI2tOY)

## Preparation

Start with a struct to hold every information in the image

```cpp
//Image.h
#include <stdint.h>
struct Image {
    uint8_t *data = NULL;
    size_t size = 0;
    int w;
    int h;
    int channels;

    Image(const char* filename); //Constructor
    ~Image(); //Deconstructor

    bool read(const char* filename); //Part of the Constructor
};
```

> - *w* and *h* are the width and height of the image in pixels
> - *channels* one for each color channel (normally 3)
> - *size = w \* h \* channels*
> - *data* is an array with 3 positions for each pixel
>   - data[0] = red value for the first pixel
>   - data[1] = green value for the first pixel
>   - data[2] = blue value for the first pixel  

```cpp
//Image.cpp includes
#define STB_IMAGE_IMPLEMENTATION
#define STB_IMAGE_WRITE_IMPLEMENTATION
#include "Image.h"
#include "../lib/stb_image.h"
#include "../lib/stb_image_write.h"
```

```cpp
//Image.cpp Constructor
Image::Image(const char *filename){ // ! Constructor
    if (read(filename)){
        size = w * h * channels;
    };
};

bool Image::read(const char *filename){ // ! Reads image
    data = stbi_load(filename, &w, &h, &channels, 0);
    return data != NULL;
};
```

> - In *stbi_load* the *0* is the *force channels* parameter, 0 if there is no forcing (don't force by default)

```cpp
//Image.cpp Deconstructor
Image::~Image(){ // ! Destructor
    stbi_image_free(data);
};
```

## Usage

Just instanciate the struct with the file path

```cpp
Image img(imgName); //instance
```

and use the *data* as an array, each pixel has 3 positions

```cpp
r[pixel] = data[pixel * 3];
g[pixel] = data[pixel * 3 + 1];
b[pixel] = data[pixel * 3 + 2];
```
