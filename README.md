##Installing openCV

Unzip the download into a directory of your choice. Then go into the ```release```  folder to do the compiling. 

We want to install openCV in our user space (not the system space), so we don't need su rights to do so. This can be achieved using

    cmake -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=/home/sjh/software/opencv-2.4.13/lib ..

then you can do 

    ./configure
    make 
    make install
   
NB actually, if you do this from the folder /home/sjh/software/opencv-2.4.13/release, you can use this without doing the make install. 

##Testing a complie outside eclipse

Following http://docs.opencv.org/2.4/doc/tutorials/introduction/linux_gcc_cmake/linux_gcc_cmake.html

We need to tell cmake where to look for the opencv libraries, because they aren't in the usual place. This can be done by setting an environment variable like this: 

    export CMAKE_PREFIX_PATH=/home/sjh/software/opencv-2.4.13/release/
  
  
(that from https://blogs.kde.org/2008/12/12/how-get-cmake-find-what-you-want-it)    
NB: you'll need to add this to your .profile if you want this environment variable to be permanent. (edit your .profile file and add this line at the bottom).

then it's just 

    cmake .
    make
  
works fine. If you want to try this, go to the opencv_eclipse/src subdirectory of this project and enter the commands above - this should build the DisplayImage executable for you. 






##Creating an eclipse CDT project

Following https://cmake.org/Wiki/CMake:Eclipse_UNIX_Tutorial option 1


###Creating a file inside eclipse

A few more commands are needed to generate an eclipse project from the above files. Switch to the bin directory and type 

    cmake -G"Eclipse CDT4 - Unix Makefiles" -D CMAKE_BUILD_TYPE=Debug ../src

This tells cmake to build an eclipse project in Debug mode from the files in ../src. 

You are now ready to import this project into eclipse, using file->import - see the link above for instructions








