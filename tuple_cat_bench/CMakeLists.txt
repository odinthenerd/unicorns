cmake_minimum_required(VERSION 3.5)
set (CMAKE_CXX_STANDARD 14)
SET(CMAKE_CXX_COMPILER /usr/bin/clang-5.0)
list(APPEND CMAKE_MODULE_PATH "~/git/metabench") #change to your metabench folder
set(CMAKE_CXX_FLAGS "${CMAKE_C_FLAGS} -stdlib=libc++")
# Actually include the module
include(metabench)

# Add new datasets
metabench_add_dataset(libcpp "src/libcpp.cpp.erb" "(1...70).step(10)")
metabench_add_dataset(libcpp1 "src/libcpp1.cpp.erb" "(1...70).step(10)")
metabench_add_dataset(epo "src/new.cpp.erb" "(1...70).step(10)")
metabench_add_dataset(epo1 "src/new1.cpp.erb" "(1...70).step(10)")
# Add a new chart
metabench_add_chart(large DATASETS libcpp epo)
metabench_add_chart(many DATASETS libcpp epo)
