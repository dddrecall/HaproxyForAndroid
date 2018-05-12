# For more information about using CMake with Android Studio, read the
# documentation: https://d.android.com/studio/projects/add-native-code.html

# Sets the minimum version of CMake required to build the native library.

cmake_minimum_required(VERSION 3.4.1)

# Creates and names a library, sets it as either STATIC
# or SHARED, and provides the relative paths to its source code.
# You can define multiple libraries, and CMake builds them for you.
# Gradle automatically packages shared libraries with your APK.

add_library( # Sets the name of the library.
             native-lib

             # Sets the library as a shared library.
             SHARED

             # Provides a relative path to your source file(s).
             src/main/cpp/native-lib.cpp )

# Searches for a specified prebuilt library and stores the path as a
# variable. Because CMake includes system libraries in the search path by
# default, you only need to specify the name of the public NDK library
# you want to add. CMake verifies that the library exists before
# completing its build.

find_library( # Sets the name of the path variable.
              log-lib

              # Specifies the name of the NDK library that
              # you want CMake to locate.
              log )

# Specifies libraries CMake should link to your target library. You
# can link multiple libraries, such as libraries you define in this
# build script, prebuilt third-party libraries, or system libraries.

target_link_libraries( # Specifies the target library.
                       native-lib

                       # Links the target library to the log library
                       # included in the NDK.
                       ${log-lib} )

#lua.a
add_library( # Sets the name of the library.
             lua

             # Sets the library as a shared library.
             STATIC

             # Provides a relative path to your source file(s).
             src/main/cpp/lua-5.3.4/src/lapi.c
             src/main/cpp/lua-5.3.4/src/lauxlib.c
             src/main/cpp/lua-5.3.4/src/lbaselib.c
             src/main/cpp/lua-5.3.4/src/lbitlib.c
             src/main/cpp/lua-5.3.4/src/lcode.c
             src/main/cpp/lua-5.3.4/src/lcorolib.c
             src/main/cpp/lua-5.3.4/src/lctype.c
             src/main/cpp/lua-5.3.4/src/ldblib.c
             src/main/cpp/lua-5.3.4/src/ldebug.c
             src/main/cpp/lua-5.3.4/src/ldo.c
             src/main/cpp/lua-5.3.4/src/ldump.c
             src/main/cpp/lua-5.3.4/src/lfunc.c
             src/main/cpp/lua-5.3.4/src/lgc.c
             src/main/cpp/lua-5.3.4/src/linit.c
             src/main/cpp/lua-5.3.4/src/liolib.c
             src/main/cpp/lua-5.3.4/src/llex.c
             src/main/cpp/lua-5.3.4/src/lmathlib.c
             src/main/cpp/lua-5.3.4/src/lmem.c
             src/main/cpp/lua-5.3.4/src/loadlib.c
             src/main/cpp/lua-5.3.4/src/lobject.c
             src/main/cpp/lua-5.3.4/src/lopcodes.c
             src/main/cpp/lua-5.3.4/src/loslib.c
             src/main/cpp/lua-5.3.4/src/lparser.c
             src/main/cpp/lua-5.3.4/src/lstate.c
             src/main/cpp/lua-5.3.4/src/lstring.c
             src/main/cpp/lua-5.3.4/src/lstrlib.c
             src/main/cpp/lua-5.3.4/src/ltable.c
             src/main/cpp/lua-5.3.4/src/ltablib.c
             src/main/cpp/lua-5.3.4/src/ltm.c
             src/main/cpp/lua-5.3.4/src/lundump.c
             src/main/cpp/lua-5.3.4/src/lutf8lib.c
             src/main/cpp/lua-5.3.4/src/lvm.c
             src/main/cpp/lua-5.3.4/src/lzio.c
             )

add_definitions(-DLUA_COMPAT_5_2 -DLUA_USE_LINUX)

include_directories (src/main/cpp/haproxy-1.8.7/include)

#ebtree.a
add_library( # Sets the name of the library.
             ebtree

             # Sets the library as a shared library.
             STATIC

             # Provides a relative path to your source file(s).
             src/main/cpp/haproxy-1.8.7/ebtree/ebtree.c
             src/main/cpp/haproxy-1.8.7/ebtree/eb32sctree.c
             src/main/cpp/haproxy-1.8.7/ebtree/eb32tree.c
             src/main/cpp/haproxy-1.8.7/ebtree/eb64tree.c
             src/main/cpp/haproxy-1.8.7/ebtree/ebmbtree.c
             src/main/cpp/haproxy-1.8.7/ebtree/ebsttree.c
             src/main/cpp/haproxy-1.8.7/ebtree/ebimtree.c
             src/main/cpp/haproxy-1.8.7/ebtree/ebistree.c
             )

#haproxy
add_executable( # Sets the name of the library.
             haproxy
             src/main/cpp/haproxy-1.8.7/src/proto_http.c
             src/main/cpp/haproxy-1.8.7/src/cfgparse.c
             src/main/cpp/haproxy-1.8.7/src/server.c
             src/main/cpp/haproxy-1.8.7/src/stream.c
             src/main/cpp/haproxy-1.8.7/src/flt_spoe.c
             src/main/cpp/haproxy-1.8.7/src/stick_table.c
             src/main/cpp/haproxy-1.8.7/src/stats.c
             src/main/cpp/haproxy-1.8.7/src/mux_h2.c
             src/main/cpp/haproxy-1.8.7/src/checks.c
             src/main/cpp/haproxy-1.8.7/src/haproxy.c
             src/main/cpp/haproxy-1.8.7/src/log.c
             src/main/cpp/haproxy-1.8.7/src/dns.c
             src/main/cpp/haproxy-1.8.7/src/peers.c
             src/main/cpp/haproxy-1.8.7/src/standard.c
             src/main/cpp/haproxy-1.8.7/src/sample.c
             src/main/cpp/haproxy-1.8.7/src/cli.c
             src/main/cpp/haproxy-1.8.7/src/stream_interface.c
             src/main/cpp/haproxy-1.8.7/src/proto_tcp.c
             src/main/cpp/haproxy-1.8.7/src/backend.c
             src/main/cpp/haproxy-1.8.7/src/proxy.c
             src/main/cpp/haproxy-1.8.7/src/tcp_rules.c
             src/main/cpp/haproxy-1.8.7/src/listener.c
             src/main/cpp/haproxy-1.8.7/src/flt_http_comp.c
             src/main/cpp/haproxy-1.8.7/src/pattern.c
             src/main/cpp/haproxy-1.8.7/src/cache.c
             src/main/cpp/haproxy-1.8.7/src/filters.c
             src/main/cpp/haproxy-1.8.7/src/vars.c
             src/main/cpp/haproxy-1.8.7/src/acl.c
             src/main/cpp/haproxy-1.8.7/src/payload.c
             src/main/cpp/haproxy-1.8.7/src/connection.c
             src/main/cpp/haproxy-1.8.7/src/raw_sock.c
             src/main/cpp/haproxy-1.8.7/src/proto_uxst.c
             src/main/cpp/haproxy-1.8.7/src/flt_trace.c
             src/main/cpp/haproxy-1.8.7/src/session.c
             src/main/cpp/haproxy-1.8.7/src/ev_select.c
             src/main/cpp/haproxy-1.8.7/src/channel.c
             src/main/cpp/haproxy-1.8.7/src/task.c
             src/main/cpp/haproxy-1.8.7/src/queue.c
             src/main/cpp/haproxy-1.8.7/src/applet.c
             src/main/cpp/haproxy-1.8.7/src/map.c
             src/main/cpp/haproxy-1.8.7/src/frontend.c
             src/main/cpp/haproxy-1.8.7/src/freq_ctr.c
             src/main/cpp/haproxy-1.8.7/src/lb_fwlc.c
             src/main/cpp/haproxy-1.8.7/src/mux_pt.c
             src/main/cpp/haproxy-1.8.7/src/auth.c
             src/main/cpp/haproxy-1.8.7/src/fd.c
             src/main/cpp/haproxy-1.8.7/src/hpack-dec.c
             src/main/cpp/haproxy-1.8.7/src/memory.c
             src/main/cpp/haproxy-1.8.7/src/lb_fwrr.c
             src/main/cpp/haproxy-1.8.7/src/lb_chash.c
             src/main/cpp/haproxy-1.8.7/src/lb_fas.c
             src/main/cpp/haproxy-1.8.7/src/hathreads.c
             src/main/cpp/haproxy-1.8.7/src/chunk.c
             src/main/cpp/haproxy-1.8.7/src/lb_map.c
             src/main/cpp/haproxy-1.8.7/src/xxhash.c
             src/main/cpp/haproxy-1.8.7/src/regex.c
             src/main/cpp/haproxy-1.8.7/src/shctx.c
             src/main/cpp/haproxy-1.8.7/src/buffer.c
             src/main/cpp/haproxy-1.8.7/src/action.c
             src/main/cpp/haproxy-1.8.7/src/h1.c
             src/main/cpp/haproxy-1.8.7/src/compression.c
             src/main/cpp/haproxy-1.8.7/src/pipe.c
             src/main/cpp/haproxy-1.8.7/src/namespace.c
             src/main/cpp/haproxy-1.8.7/src/sha1.c
             src/main/cpp/haproxy-1.8.7/src/hpack-tbl.c
             src/main/cpp/haproxy-1.8.7/src/hpack-enc.c
             src/main/cpp/haproxy-1.8.7/src/uri_auth.c
             src/main/cpp/haproxy-1.8.7/src/time.c
             src/main/cpp/haproxy-1.8.7/src/proto_udp.c
             src/main/cpp/haproxy-1.8.7/src/arg.c
             src/main/cpp/haproxy-1.8.7/src/signal.c
             src/main/cpp/haproxy-1.8.7/src/protocol.c
             src/main/cpp/haproxy-1.8.7/src/lru.c
             src/main/cpp/haproxy-1.8.7/src/hdr_idx.c
             src/main/cpp/haproxy-1.8.7/src/hpack-huff.c
             src/main/cpp/haproxy-1.8.7/src/mailers.c
             src/main/cpp/haproxy-1.8.7/src/h2.c
             src/main/cpp/haproxy-1.8.7/src/base64.c
             src/main/cpp/haproxy-1.8.7/src/hash.c
             src/main/cpp/haproxy-1.8.7/src/ev_epoll.c
             src/main/cpp/haproxy-1.8.7/src/hlua.c
             src/main/cpp/haproxy-1.8.7/src/hlua_fcn.c
             )

target_link_libraries(haproxy ebtree)
target_link_libraries(haproxy lua)
target_link_libraries(haproxy dl)

target_include_directories (haproxy PUBLIC src/main/cpp/haproxy-1.8.7/ebtree)
target_include_directories (haproxy PUBLIC src/main/cpp/lua-5.3.4/src)

target_compile_definitions(haproxy PUBLIC -DENABLE_EPOLL)
target_compile_definitions(haproxy PUBLIC -DCONFIG_HAPROXY_VERSION=\"1.8.7\")
target_compile_definitions(haproxy PUBLIC -DCONFIG_HAPROXY_DATE=\"2018\")
target_compile_definitions(haproxy PUBLIC -DUSE_LUA)

# set binary output folder to Android assets folder
set(EXECUTABLE_OUTPUT_PATH "${CMAKE_CURRENT_SOURCE_DIR}/src/main/assets/${ANDROID_ABI}")
