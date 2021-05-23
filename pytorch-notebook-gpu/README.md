Run docker with:

```
sudo docker run -u $(id -u):$(id -g) -v $PWD:/workspace --gpus all -it -p 8888:8888 --name pytorch-notebook --rm jupyter-pytorch
```

Container based of:
https://github.com/jxcodetw/docker-jupyter-pytorch
