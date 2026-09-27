cmake_minimum_required(VERSION 3.21)
project(
  llamaRouter
  VERSION 0.1.0
  DESCRIPTION "VRAM-aware inference router for llama.cpp"
  LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

# --- Core library -------------------------------------------------------------
add_library(llamarouter_core
  src/router.cpp
  src/config.cpp
  src/vram/vram_budget.cpp
  src/vram/vram_monitor.cpp
  src/queue/request_queue.cpp
)


# --- Executable ----------------------------------------------------------------
add_executable(llamarouter src/main.cpp)
target_link_libraries(llamarouter PRIVATE llamarouter_core)