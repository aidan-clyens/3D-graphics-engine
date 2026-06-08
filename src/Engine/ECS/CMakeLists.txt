project(ECS)

add_library(${PROJECT_NAME} STATIC)

target_sources(${PROJECT_NAME}
  PUBLIC
  FILE_SET HEADERS
    BASE_DIRS
      ${CMAKE_CURRENT_SOURCE_DIR}/include
    FILES
        include/DynamicCharacterController.h
        include/ECS.h
        include/Mesh.h
        include/MeshInstances.h
        include/Model.h
        include/Rigidbody.h
)

target_sources(${PROJECT_NAME} PRIVATE
    src/DynamicCharacterController.cpp
    src/ECS.cpp
    src/Mesh.cpp
    src/MeshInstances.cpp
    src/Model.cpp
    src/Rigidbody.cpp
)

target_include_directories(${PROJECT_NAME}
  PUBLIC
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
    $<BUILD_INTERFACE:${CMAKE_SOURCE_DIR}/include>
)

target_link_libraries(${PROJECT_NAME} PUBLIC
    glfw glad::glad glm::glm assimp::assimp BulletDynamics BulletCollision LinearMath ${GLFW_LIBRARIES}
)

set_target_properties(${PROJECT_NAME} PROPERTIES LINKER_LANGUAGE CXX)