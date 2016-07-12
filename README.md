###Copyright
The project is modified based on the original version of DLoopDetector available [here](http://webdiis.unizar.es/~dorian/index.php?p=33) or [here](https://github.com/dorian3d/DLoopDetector), so all the stuff are copyrighted by [Dorian Gálvez López](http://webdiis.unizar.es/~dorian/index.php)

###Modification
Our implementation differs from the origin in following aspects:
- All the folders and files are reoganized with CMake tool chain, so a couple of CMakeLists.txt are added.
- The DBow2 is integrated with DLoopDetector. They are separated projects at Dorian's homepage.
- Dorian has upgraded his code compling with OpenCV3.x, but my code still works with OpenCV2.x. Note that the new version of OpenCV is not backwardly compatible.
- The shell 'create_eclipse_project' could generate Eclipse project, making debugging with an IDE possible.

###How to compile
It can be compiled like the normal CMake organized project
```
mkdir build
cd build
cmake ..
make
```

###How to use
After the compiling, the visual words should be extracted based on your image sequence in the following way
```
 ./demo_dbow2 <image dir> <output voc file> <output voc db file>
``` 
It might take fairly long time according to the scale of your data. Then the DLoopDetector can be run with the command
```
./demo_surf <image dir> <voc_file> <pose_file> <loop_file> <image_width> <image_height>
``` 

###How to use on `Kylin@Wallaby`
A couple of data are available on Kylin, but root permission is needed as the data are in the shared folder between Wallaby host and Kylin slave. The following instructions can help MPIG members to run the demo with different datasets once the project is built.

####KITTI00
* Create directories for visual words and detected loop results
```
mkdir bow loop  
``` 
* Generate visual words
```
./bin/demo_bow2 /media/sf_Kylin/RawData/KITTI/dataset/sequences/00/left ./bow/kitti00_voc.yml.gz ./bow/kitti00_db.yml.gz
```
* Seek loops after the BoW is ready
```
./bin/demo_surf /media/sf_Kylin/RawData/KITTI/dataset/sequences/00/left ./bow/kitti00_vol.yml.gz /media/sf_Kylin/trajectory/kitti00_trajectory.txt ./loop/kitti00loops.txt 1241 376
```
####KITTI01
```
./bin/demo_bow2 /media/sf_Kylin/RawData/KITTI/dataset/sequences/01/left ./bow/kitti01_voc.yml.gz ./bow/kitti01_db.yml.gz
```
```
./bin/demo_surf /media/sf_Kylin/RawData/KITTI/dataset/sequences/01/left ./bow/kitti01_vol.yml.gz /media/sf_Kylin/trajectory/kitti01_trajectory.txt ./loop/kitti01loops.txt 1241 376
```
####KITTI02
```
./bin/demo_bow2 /media/sf_Kylin/RawData/KITTI/dataset/sequences/02/left ./bow/kitti02_voc.yml.gz ./bow/kitti02_db.yml.gz
```
```
./bin/demo_surf /media/sf_Kylin/RawData/KITTI/dataset/sequences/02/left ./bow/kitti02_vol.yml.gz /media/sf_Kylin/trajectory/kitti02_trajectory.txt ./loop/kitti02loops.txt 1241 376
```
###How to generate the trajectory
The pose file is only for visualization. It can be made based on GPS data or IMU data. In our application, the robot trajectory is the two translation components estimated by the stereo version of [Libviso2](http://www.cvlibs.net/software/libviso/).

**For more information, please contact [szl@mpig.com.cn](http://mpig.com.cn)**  
