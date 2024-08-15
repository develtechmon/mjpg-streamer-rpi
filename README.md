# Getting Started

This is userguide on how i install this package inside my `rpi zero 2`. 
Details as follow:

* Flash using `rpi zero human following drone image`.
* This image is using `bullseye` 32 bit version

# Step 1: Clone `mjpg-streamer-rpi`.

Inside your `rpi zero 2`, please do the following
```
cd ~ (To enter to home directory)
git clone https://github.com/develtechmon/mjpg-streamer-rpi.git
```

# Step 2: Enable `rpi camera legacy`

I find this is very interesting, to have a working `stream` and even also `aruco camera` calibration,
we have to enable `camera legacy`.

This can be done as follow
```
sudo raspi-config
Interface --> Legacy Camera (Please Enable legacy camera support and hit YES)

Finish and reboot the rpi
```

# Step 3: Install the `mjpeg package`

Please install below package
```
sudo apt-get install cmake libjpeg9-dev
```

Next
```
sudo apt-get install gcc g++
```

Then compile the package
```
cd mjpg-streamer-experimental
make
sudo make install
```
# Step 4: Run the Stream

To run the stream, please ensure you're still within the directory. If yes, then run the following command
```
/usr/local/bin/mjpg_streamer -i "input_uvc.so -r 640x480 -d /dev/video0 -f 24 -q 80" -o "output_http.so -p 8080 -w /usr/local/share/mjpg-streamer/www"
```

At this point, you should the `working log`.

From your `browser`, run the following to see the `stream`
```
http://172.20.10.2:8080/

Remember, this is your RPI Ip address and 8080 is the port number
```

CONGRATS !
