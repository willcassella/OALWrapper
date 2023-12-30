load("//defs.bzl", "global_compiler_flags")
load("//defs.bzl", "global_linker_flags")

cxx_library(
    name = "OALWrapper",
    visibility = ["PUBLIC"],
    srcs = [
        "sources/OAL_AudioData.cpp",
        "sources/OAL_Buffer.cpp",
        "sources/OAL_CustomStream.cpp",
        "sources/OAL_Device.cpp",
        "sources/OAL_EFX.cpp",
        "sources/OAL_EFXManager.cpp",
        "sources/OAL_Effect.cpp",
        "sources/OAL_EffectSlot.cpp",
        "sources/OAL_Effect_Reverb.cpp",
        "sources/OAL_Filter.cpp",
        "sources/OAL_Helper.cpp",
        "sources/OAL_Init.cpp",
        "sources/OAL_Loaders.cpp",
        "sources/OAL_LoggerObject.cpp",
        "sources/OAL_OggSample.cpp",
        "sources/OAL_OggStream.cpp",
        "sources/OAL_Playback.cpp",
        "sources/OAL_Sample.cpp",
        "sources/OAL_Source.cpp",
        "sources/OAL_SourceManager.cpp",
        "sources/OAL_Stream.cpp",
        "sources/OAL_Types.cpp",
        "sources/OAL_WAVSample.cpp",
    ],
    exported_deps = [
        "//OALWrapper/include:headers",
    ],
    compiler_flags = select({
        "config//os:linux": global_compiler_flags + [
            "-I/usr/include/SDL",
        ],
        "config//os:macos": global_compiler_flags + [
            "-isystem",
            "/opt/homebrew/include",
            "-isystem",
            "/opt/homebrew/include/SDL",
        ],
    }),
    exported_linker_flags = select({
        "config//os:linux":  [
        ],
        "config//os:macos": [
            "-L/opt/homebrew/opt/openal-soft/lib",
            "-lopenal",
            "-L/opt/homebrew/lib",
            "-lSDL",
            "-lvorbisfile",
        ]
    }),
    linker_flags = global_linker_flags,
    link_style = "static",
)
