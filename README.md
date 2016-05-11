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

(6) On the container's bash prompt, ensure you are in /root

$ pwd
/root

(7) Create a new file ".cloudfuse" in the same directory and add the following contents :

username=[your username]
api_key=[key or password string]
authurl=https://dal05.objectstorage.softlayer.net/auth/v1.0/

Please change the authurl as per the DC you want to connect to.

(8) Create the mount directory and mount the storage :

$ mkdir /storage
$ cloudfuse /storage

(9) Start accessing the Softlayer object storage in the container at the mounted directory!
