# DPDK
How to install DPDK in Linux and run DPDK

1. Check NIC if it is possible to use DPDK

![NIC check](https://user-images.githubusercontent.com/61117544/113512091-0703e800-959e-11eb-811c-b7c1001b8964.JPG)
My linux uses e1000 that could run well.

2. Download DPDK file from dpdk.org

I used the version dpdk-20.08
//wget http://fast.dpdk.org/rel/dpdk-20.08.tar.xz

3. unzip it and enter its directory.
//tar xf dpdk-20.08.tar.xz
//cd dpdk-20.08.tar.xz

4. DPDK recommends to use meson build and ninja build.
However the version of apt meson is 0.45 which is lower than 0.47.
DPDK needs version of meson more than 0.48.

 4-1. remove apt meson. 
 //sudo apt purge meson -y
 4-2. install using pip3(the version of meson is 0.53 now)
 //sudo pip3 install meson
 4-3. path update
 //PATH=$PATH:/home/{$username}/.local/bin

5. At that directory writes commands
//meson build (it tooks 3~5 minutes)
//ninja -C build (it also took 5~6 minutes)

6. Include meson build
//meson -Dexamples=all build

7. Make huge pages
![hugepageadd](https://user-images.githubusercontent.com/61117544/113512340-23eceb00-959f-11eb-81a2-e92611faac6c.jpg)

I made 8 huge pages with 2048KB size.
![hugecheck](https://user-images.githubusercontent.com/61117544/113512357-441caa00-959f-11eb-9d32-f9dbeecfbdba.jpg)

8. Check NIC to bind
//sudo ./dpdk-devbind.py --status
![last](https://user-images.githubusercontent.com/61117544/113512415-82b26480-959f-11eb-94c0-c1e0892a1499.JPG)

9. Finally bind it!
