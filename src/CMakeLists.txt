# Alle Quellen einsammeln
file(GLOB_RECURSE SRC CONFIGURE_DEPENDS
  ${CMAKE_CURRENT_SOURCE_DIR}/*.cpp
)

# SFML 2 finden
find_package(SFML 2 REQUIRED COMPONENTS system window graphics)

# Executable anlegen
add_executable(SpaceInvaders ${SRC})

# C++17 für dieses Target absichern
target_compile_features(SpaceInvaders PRIVATE cxx_std_17)

# Gegen SFML 2 linken
target_link_libraries(SpaceInvaders PRIVATE
  sfml-graphics
  sfml-window
  sfml-system
)

# Installation ins bin-Verzeichnis
install(TARGETS SpaceInvaders RUNTIME DESTINATION bin)
