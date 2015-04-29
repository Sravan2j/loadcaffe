loadcaffe
=========
##### This branch supports old version of Caffe that uses V1LayerParameter like the models in Caffe [Model Zoo](https://github.com/BVLC/caffe/wiki/Model-Zoo).

Load Caffe networks in Torch7

There is no Caffe dependency, only protobuf has to be installed. In Ubuntu do:

```
sudo apt-get install libprotobuf-dev protobuf-compiler
```

Then install the package itself do:

```
luarocks install loadcaffe
```

To load a network do:

```lua
require 'loadcaffe'

model = loadcaffe.load('deploy.prototxt', 'bvlc_alexnet.caffemodel', 'ccn2')
```

Models from Caffe [Model Zoo](https://github.com/BVLC/caffe/wiki/Model-Zoo):

| Network  | ccn2 | cunn | cudnn |
| ------------- | :-------------: | :-------: | :---: |
| bvlc_alexnet | + | - | + |
| bvlc_reference_caffenet | + | - | + |
| bvlc_reference_rcnn_ilsvrc13 | + | - | + |
| [finetune_flickr_style](https://gist.github.com/sergeyk/034c6ac3865563b69e60) | + | - | + |
| [VGG_CNN_S](https://gist.github.com/ksimonyan/fd8800eeb36e276cd6f9)  | +  | + | + |
| [VGG_CNN_M](https://gist.github.com/ksimonyan/f194575702fae63b2829)  | +  | + | + |
| [VGG_CNN_M_2048](https://gist.github.com/ksimonyan/78047f3591446d1d7b91)  | +  | + | + |
| [VGG_CNN_M_1024](https://gist.github.com/ksimonyan/f0f3d010e6d5f0100274)  | +  | + | + |
| [VGG_CNN_M_128](https://gist.github.com/ksimonyan/976847408258292576a1)  | +  | + | + |
| [VGG_CNN_F](https://gist.github.com/ksimonyan/a32c9063ec8e1118221a)  | +  | + | + |
| [VGG ILSVRC-2014 16-layer](https://gist.github.com/ksimonyan/211839e770f7b538e2d8) | + | + | + |
| [VGG ILSVRC-2014 19-layer](https://gist.github.com/ksimonyan/3785162f95cd2d5fee77) | + | + | + |
| [Network-in-Network Imagenet](https://gist.github.com/mavenlin/d802a5849de39225bcc6) | - | + | + |
| [Network-in-Network CIFAR-10](https://gist.github.com/mavenlin/e56253735ef32c3c296d) | - | + | + |
| MNIST LeNet | - | + | + |

If you want to use nn and BDHW routines only, please install https://github.com/szagoruyko/imagine-nn, which has ceil max-pooling and local response normalization. Note that it is not required for ccn2.

You can also use Caffe inside Torch with this: https://github.com/szagoruyko/torch-caffe-binding However you can't use both loadcaffe in caffe in one torch session.

An example of using the package is in [examples/mnist_lenet.lua](examples/mnist_lenet.lua). After running script to train lenet model in Caffe you can easily load and test it in Torch7.

Rights to caffe.proto belong to the University of California.
