
- use clangd extension for intellisense and compile
- use c/c++ microsoft extension for debug
- use cmake extension for build compile add CMakeLists.txt to root dir after updating

## expected layout
project/
├── CMakeLists.txt
├── src/
│   └── main.cpp
├── include/
└── build/

## multi target shared libraries
project/
├── CMakeLists.txt
├── include/
│   └── common/
│       ├── config.h
│       └── protocol.h
├── src/
│   ├── common/
│   │   ├── config.cpp
│   │   └── protocol.cpp
│   ├── frontend/
│   │   ├── main.cpp
│   │   └── ui.cpp
│   └── backend/
│       ├── main.cpp
│       └── server.cpp
└── build/
