---
title: Reglas predefinidas
ms.date: 11/04/2016
helpviewer_keywords:
- rules, predefined
- NMAKE program, predefined rules
- predefined rules in NMAKE
ms.assetid: 638cdc3f-4aba-4b4f-96e3-ad65b0364f12
ms.openlocfilehash: 7a922a239306f10121791caa8f9f088cea88c019
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62319452"
---
# <a name="predefined-rules"></a>Reglas predefinidas

Las reglas de inferencia predefinidas utilizan macros de comando y de opciones proporcionadas por NMAKE.

|Regla|Comando|Default<br /><br /> predeterminada|por lotes<br /><br /> Regla|Plataforma donde se ejecuta NMAKE|
|----------|-------------|------------------------|--------------------|----------------------------|
|.asm.exe|$(AS) $(AFLAGS) $&LT;|ml $<|No|x86|
|.asm.obj|$(AS) $(AFLAGS) /c $<|ml /c $<|sí|x86|
|.asm.exe|$(AS) $(AFLAGS) $&LT;|ml64 $<|No|x64|
|.asm.obj|$(AS) $(AFLAGS) /c $<|ml64 /c $<|sí|x64|
|.c.exe|$(CC) $(CFLAGS) $&LT;|CL $<|No|todo|
|.c.obj|$(CC) $(CFLAGS) /c $<|cl /c $<|sí|todo|
|.cc.exe|$(CC) $(CFLAGS) $&LT;|CL $<|No|todo|
|.cc.obj|$(CC) $(CFLAGS) /c $<|cl /c $<|sí|todo|
|.cpp.exe|$(CPP) $(CPPFLAGS) $&LT;|CL $<|No|todo|
|.cpp.obj|$(CPP) $(CPPFLAGS) /c $<|cl /c $<|sí|todo|
|.cxx.exe|$(CXX) $(CXXFLAGS) $&LT;|CL $<|No|todo|
|.cxx.obj|$(CXX) $(CXXFLAGS) /c $<|cl /c $<|sí|todo|
|.rc.res|$(RC) $(RFLAGS) /r $<|rc /r $<|No|todo|

## <a name="see-also"></a>Vea también

[Reglas de inferencia](inference-rules.md)
