cmake_minimum_required(VERSION 3.14)

# set(CMAKE_CXX_STANDARD 17)
# set(CMAKE_CXX_STANDARD_REQUIRED ON)
# set(CMAKE_CXX_EXTENSIONS OFF)

project(poco-playground)


# find_package(OpenSSL CONFIG REQUIRED)
# message("OpenSSL found: ${OpenSSL_FOUND}")
# # set(OpenSSL::Crypto Crypto)

find_package(Poco REQUIRED COMPONENTS Net Util JSON) 
if (Poco_FOUND)
    message("Poco found")
else (Poco_FOUND)
    message("Poco not found")
endif()

SET(CMAKE_EXE_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS} -static")

add_executable(${PROJECT_NAME}
    "src/main.cpp"
)

target_link_libraries(${PROJECT_NAME} Poco::Util Poco::JSON Poco::Net)