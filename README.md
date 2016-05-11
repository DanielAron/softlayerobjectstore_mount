This repo includes the Dockerfile, to create a docker image capable of mounting the IBM Softlayer object storage.

Follow these instructions to create the image :

(1) Clone the github project

$ git clone https://github.com/syallapr/softlayerobjectstore_mount.git

(2) Look for the folder "softlayerobjectstore_mount" and cd into it.

(3) Build the image :

$ docker build .

(4) You should see the image built and visible, when you run :

$ docker images

(5) Run the container :

$ docker run --cap-add SYS_ADMIN --privileged --device /dev/fuse:/dev/fuse:mrw -i -t <ImageID>
