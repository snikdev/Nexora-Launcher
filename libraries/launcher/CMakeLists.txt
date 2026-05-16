cmake_minimum_required(VERSION 3.15)
project(launcher Java)
find_package(Java 1.7 REQUIRED COMPONENTS Development)

include(UseJava)
set(CMAKE_JAVA_JAR_ENTRY_POINT org.nexoralauncher.EntryPoint)
set(CMAKE_JAVA_COMPILE_FLAGS -target 7 -source 7)

set(SRC
    org/nexoralauncher/EntryPoint.java
    org/nexoralauncher/launcher/Launcher.java
    org/nexoralauncher/launcher/impl/AbstractLauncher.java
    org/nexoralauncher/launcher/impl/StandardLauncher.java
    org/nexoralauncher/exception/ParameterNotFoundException.java
    org/nexoralauncher/exception/ParseException.java
    org/nexoralauncher/utils/Parameters.java
    org/nexoralauncher/utils/ReflectionUtils.java
    org/nexoralauncher/utils/logging/Level.java
    org/nexoralauncher/utils/logging/Log.java
    org/nexoralauncher/legacy/LegacyProxy.java
)

set(LEGACY_SRC
    legacy/org/nexoralauncher/legacy/LegacyFrame.java
    legacy/org/nexoralauncher/legacy/LegacyLauncher.java
    legacy/org/nexoralauncher/legacy/fix/online/Handler.java
    legacy/org/nexoralauncher/legacy/fix/online/OnlineFixes.java
    legacy/org/nexoralauncher/legacy/fix/online/OnlineModeFix.java
    legacy/org/nexoralauncher/legacy/fix/online/SkinFix.java
    legacy/org/nexoralauncher/legacy/utils/Base64.java
    legacy/org/nexoralauncher/legacy/utils/api/MojangApi.java
    legacy/org/nexoralauncher/legacy/utils/api/Texture.java
    legacy/org/nexoralauncher/legacy/utils/json/JsonParseException.java
    legacy/org/nexoralauncher/legacy/utils/json/JsonParser.java
    legacy/org/nexoralauncher/legacy/utils/url/ByteArrayUrlConnection.java
    legacy/org/nexoralauncher/legacy/utils/url/UrlUtils.java
    legacy/net/minecraft/Launcher.java
    legacy/org/nexoralauncher/legacy/LegacyProxy.java
)

add_jar(NewLaunch ${SRC})
add_jar(NewLaunchLegacy ${LEGACY_SRC} INCLUDE_JARS NewLaunch)
install_jar(NewLaunch "${JARS_DEST_DIR}")
install_jar(NewLaunchLegacy "${JARS_DEST_DIR}")
