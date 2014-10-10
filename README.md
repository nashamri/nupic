![docker_nupic](http://www.nass3r.com/images/docker_nupic.png")

# Overview
This is a docker image that comes with the following:
- [NuPIC](https://github.com/numenta/nupic)
- [NuPIC Studio](https://github.com/nupic-community/nupic.studio)
- [iPython notebook](https://github.com/ipython/ipython)
- Matplotlib
- MySQL server

# How to use it?
1.  Install docker and make sure it's running, more info (http://www.docker.com/)
2.  Pull the image
    ````
    docker pull nashamri/nupic
    ````
3. Run the image
    ```
    docker run -ti --net=host --rm -v /tmp/.X11-unix:/tmp/.X11-unix -e DISPLAY=unix$DISPLAY --privileged nashamri/nupic
    ```
###Explaninations
    * `--net=host`: allow the container to use the hosts network
    * `--rm`: to delete the image after exiting
    * `-v /tmp/.X11-unix:/tmp/.X11-unix -e DISPLAY=unix$DISPLAY`: to let the container access the host's X server
    * `--privileged`: when using NuPIC Studio, this might provide hardware acceleration for OpenGL. I only tested this on Intel graphics

4. Inside the image, you might need to start MySQL server to get the examples and swarming working
    ```
    service mysql start
    ```
5. To run an iPyhon notebook
    ```
    ipython notebook
    ```
6. To run NuPIC Studio
    ```
    nustudio
    ```
