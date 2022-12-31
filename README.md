pacman -Sy
#pacman -S --needed $(cat packages.txt) 
cd mingw-w64-boost && MINGW_ARCH=mingw64 makepkg-mingw -sLf && 			pacman -U mingw-w64-x86_64-boost-1.80.0-1-any.pkg.tar.zst
cd ../mingw-w64-bullet && MINGW_ARCH=mingw64 makepkg-mingw -sLf && 		pacman -U mingw-w64-x86_64-bullet-3.24-3-any.pkg.tar.zst
cd ../mingw-w64-OpenSceneGraph && MINGW_ARCH=mingw64 makepkg-mingw -sLf && 	pacman -U mingw-w64-x86_64-OpenSceneGraph-3.6.5-20-any.pkg.tar.zst
cd ../mingw-w64-mygui && MINGW_ARCH=mingw64 makepkg-mingw -sLf && 		pacman -U mingw-w64-x86_64-mingw-w64-mygui-3.4.1-any.pkg.tar.zst
cd ../mingw-w64-openmw


cd build
cmake ../ -DCMAKE_INSTALL_PREFIX="." -DCMAKE_BUILD_TYPE=Release -DBUILD_OSG_PLUGINS_BY_DEFAULT=0 -DBUILD_OSG_PLUGIN_OSG=1 -DBUILD_OSG_PLUGIN_DAE=1 -DBUILD_OSG_PLUGIN_DDS=1 -DBUILD_OSG_PLUGIN_TGA=1 -DBUILD_OSG_PLUGIN_BMP=1 -DBUILD_OSG_PLUGIN_JPEG=1 -DBUILD_OSG_PLUGIN_PNG=1 -DBUILD_OSG_PLUGIN_FREETYPE=1 -DBUILD_OSG_DEPRECATED_SERIALIZERS=0 -DOPENMW_LTO_BUILD=1 -GNinja
ninja