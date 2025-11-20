cmake_minimum_required(VERSION 3.27)
project(TrabalhoPratico_POO)

set(CMAKE_CXX_STANDARD 20)

# Buscar automaticamente todos os arquivos .cpp, excluindo a pasta de build
file(GLOB_RECURSE SOURCES "./*.cpp")
file(GLOB_RECURSE EXCLUDE_SOURCES "./cmake-build-debug/*.cpp")
list(REMOVE_ITEM SOURCES ${EXCLUDE_SOURCES})

# Adicionar os diretórios de include
include_directories(
        Buffer
        Cell
        Caravans
        City
        Items
        Terrain
        Desert
)

# Criar o executável principal
add_executable(TrabalhoPratico_POO ${SOURCES})
