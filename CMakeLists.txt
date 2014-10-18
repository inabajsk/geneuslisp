cmake_minimum_required(VERSION 2.8.3)
project(geneuslisp)
find_package(catkin REQUIRED COMPONENTS genmsg)

catkin_package(
  CATKIN_DEPENDS genmsg
  CFG_EXTRAS geneuslisp-extras.cmake
)

add_subdirectory(scripts)

file(WRITE ${CATKIN_DEVEL_PREFIX}/${GENMSG_LANGS_DESTINATION}/geneuslisp "EusLisp")
install(FILES ${CATKIN_DEVEL_PREFIX}/${GENMSG_LANGS_DESTINATION}/geneuslisp
  DESTINATION ${GENMSG_LANGS_DESTINATION})

# drop marker file to prevent rospack from spending time on crawling this folder
file(WRITE ${CATKIN_DEVEL_PREFIX}/share/roseus/rospack_nosubdirs "")
install(FILES ${CATKIN_DEVEL_PREFIX}/share/roseus/rospack_nosubdirs
  DESTINATION share/euslisp)

catkin_python_setup()
