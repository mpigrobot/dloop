###Copyright
The project is modified based on the original version of DLoopDetector available [here](http://webdiis.unizar.es/~dorian/index.php?p=33), so all the stuff are copyrighted by [Dorian Gálvez López](http://webdiis.unizar.es/~dorian/index.php)

###Modification
Our implementation differs from the origin in following aspects:
- All the folders and files are reoganized with CMake tool chain, so a couple of CMakeLists.txt are added.
- The DBow2 is integrated with DLoopDetector. They are separated projects at Dorian's homepage.

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

###The demo shells
Two shells in the folder 'shell@Kylin@Wallaby' can help the MPIG members to run the demo quickly. Please generate the visual BoW firstly by running 'makeBow_malaga07.sh' and then check the trajectory loop contained in the same data with 'detectLoop_malaga07.sh'. PLS NOTE that the path of image data is only valid on the MPIG server Kylin@Wallaby, so the shells can't work on other host.

**For more information, please contact [szl@mpig.com.cn](http://mpig.com.cn)**  
