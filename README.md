

Opencv 3.4.12
    mkdir build && cd build
    cmake -D CMAKE_BUILD_TYPE=RELEASE -DENABLE_PRECOMPILED_HEADERS=OFF -D CMAKE_INSTALL_PREFIX=/usr/local -D INSTALL_C_EXAMPLES=OFF -D INSTALL_PYTHON_EXAMPLES=OFF -D WITH_TBB=ON -D WITH_V4L=ON -D WITH_QT=OFF -D WITH_OPENGL=ON -D WITH_CUDA=OFF -D BUILD_EXAMPLES=OFF ..
    make -j4
    sudo make install
    
    


caffe

  3) make sure caffe doesn't have clip_layer. If it is there delete it following these steps:
  
      3.1) remove clip_layer.hpp and clip_layer.cpp from caffe_root/src/caffe/layers.
   
      3.2) In caffe_root/src/caffe/layers/clip_layer.cu comment out the include and the two templates and the instantiate. Comment out the     include in caffe_root/src/caffe/layer_factory.cpp.
   
       3.3) in src/caffe/proto/caffe.proto comment out the ClipParameter message and the optional clipparameter.
       If there are any other errors just comment out the source line.
   


for caffe to find cuda ?
Open the file “cmake/Cuda.cmake”. Find "file(READ ${CUDNN_INCLUDE}/cudnn.h CUDNN_VERSION_FILE_CONTENTS)",and replace "cudnn.h" with "cudnn_version.h".
 
 /usr/local/cuda-11.3/lib64 in zb ***.backup umbenennen, damit alles richtig gefunden wird

cmake -DOpenCV_DIR=/home/fabian/opencv/opencv-3.4.12/build ..
 
??? cmake -DProtobuf_LIBRARY_DEBUG=/home/fabian/installs/protobuf/protobuf-3.1.0/src/.libs/libprotobuf.so  -DProtobuf_PROTOC_EXECUTABLE=/home/fabian/installs/protobuf/protobuf-3.1.0/src/.libs/protoc -DProtobuf_LIBRARY_RELEASE=/home/fabian/installs/protobuf/protobuf-3.1.0/src/.libs/libprotobuf.a  -DProtobuf_LITE_LIBRARY_RELEASE=/home/fabian/installs/protobuf/protobuf-3.1.0/src/.libs/libprotobuf-lite.a -DBOOST_INCLUDEDIR=/home/fabian/installs/boost_1_58_0/  -DBOOST_LIBRARYDIR=/home/fabian/installs/boost_1_58_0/stage/lib -DProtobuf_INCLUDE_DIR=/home/fabian/installs/protobuf/protobuf-3.1.0/src/ -DProtobuf_PROTOC_LIBRARY_RELEASE=/home/fabian/installs/protobuf/protobuf-3.1.0/src/.libs/libprotoc.so -DCUDNN_INCLUDE=/usr/local/cuda-11.3/include/ .. 


 

5) To compile xnect project:
 
   cmake -DOpenCV_DIR=/home/fabian/opencv/opencv-3.4.12/build -DCaffe_DIR=/usr/bin/caffe/build ..
   
