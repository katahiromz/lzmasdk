add_executable(7zDec
  7zAlloc.c
  7zBuf.c
  7zCrc.c
  7zCrcOpt.c
  7zFile.c
  7zDec.c
  7zArcIn.c
  7zStream.c
  Bcj2.c
  Bra.c
  Bra86.c
  BraIA64.c
  CpuArch.c
  Delta.c
  Lzma2Dec.c
  LzmaDec.c
  Ppmd7.c
  Ppmd7Dec.c
  Util/7z/7zMain.c
  Util/7z/Precomp.c)

add_library(lzmasdk STATIC
  Util/Lzma/LzmaUtil.c
  Alloc.c
  LzFind.c
  LzFindMt.c
  LzmaDec.c
  LzmaEnc.c
  7zFile.c
  7zStream.c
  Threads.c)

add_library(lzmalib SHARED
  Util/LzmaLib/LzmaLibExports.c
  Util/LzmaLib/LzmaLib.def
  Alloc.c
  LzFind.c
  LzFindMt.c
  LzmaDec.c
  LzmaEnc.c
  LzmaLib.c
  Threads.c
  Util/LzmaLib/resource.rc)
set_target_properties(lzmalib PROPERTIES OUTPUT_NAME "lzmalib")
set_target_properties(lzmalib PROPERTIES PREFIX "")

add_executable(7zS2.sfx WIN32
  7zAlloc.c
  7zArcIn.c
  7zBuf.c
  7zBuf2.c
  7zCrc.c
  7zCrcOpt.c
  7zFile.c
  7zDec.c
  7zStream.c
  Bcj2.c
  Bra.c
  Bra86.c
  BraIA64.c
  CpuArch.c
  Delta.c
  DllSecur.c
  Lzma2Dec.c
  LzmaDec.c
  Util/SfxSetup/SfxSetup.c
  Util/SfxSetup/resource.rc)

add_executable(7zS2con.sfx
  7zAlloc.c
  7zArcIn.c
  7zBuf.c
  7zBuf2.c
  7zCrc.c
  7zCrcOpt.c
  7zFile.c
  7zDec.c
  7zStream.c
  Bcj2.c
  Bra.c
  Bra86.c
  BraIA64.c
  CpuArch.c
  Delta.c
  DllSecur.c
  Lzma2Dec.c
  LzmaDec.c
  Util/SfxSetup/SfxSetup.c
  Util/SfxSetup/resource.rc)
target_compile_definitions(7zS2con.sfx PRIVATE -D_CONSOLE)

install(TARGETS 7zDec DESTINATION bin)
install(TARGETS lzmasdk lzmalib DESTINATION lib)
install(FILES
    7z.h
    7zAlloc.h
    7zBuf.h
    7zCrc.h
    7zFile.h
    7zTypes.h
    7zVersion.h
    Aes.h
    Alloc.h
    Bcj2.h
    Bra.h
    Compiler.h
    CpuArch.h
    Delta.h
    DllSecur.h
    LzFind.h
    LzFindMt.h
    LzHash.h
    Lzma2Dec.h
    Lzma2DecMt.h
    Lzma2Enc.h
    Lzma86.h
    LzmaDec.h
    LzmaEnc.h
    LzmaLib.h
    MtCoder.h
    MtDec.h
    Ppmd.h
    Ppmd7.h
    Precomp.h
    RotateDefs.h
    Sha256.h
    Sort.h
    Threads.h
    Xz.h
    XzCrc64.h
    XzEnc.h
    DESTINATION include/lzmasdk)
