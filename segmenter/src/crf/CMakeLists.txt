INCLUDE_DIRECTORIES(${SOURCE_DIR})
ADD_EXECUTABLE(crf main.cc crf.cc ../logging.cc ../training_utils.cc ../utils.cc ../corpus.cc)
target_link_libraries(crf cnn glog ${Boost_LIBRARIES})
