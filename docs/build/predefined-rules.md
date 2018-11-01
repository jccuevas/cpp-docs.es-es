---
title: Reglas predefinidas
ms.date: 11/04/2016
helpviewer_keywords:
- rules, predefined
- NMAKE program, predefined rules
- predefined rules in NMAKE
ms.assetid: 638cdc3f-4aba-4b4f-96e3-ad65b0364f12
ms.openlocfilehash: b4b8ca7b0126ca42b2144aa094e7f766f6344b2a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50609696"
---
# <a name="predefined-rules"></a>Reglas predefinidas

Las reglas de inferencia predefinidas utilizan macros de comando y de opciones proporcionadas por NMAKE.

|Regla|Comando|Default<br /><br /> predeterminada|por lotes<br /><br /> Regla|Plataforma donde se ejecuta NMAKE|
|----------|-------------|------------------------|--------------------|----------------------------|
|.asm.exe|$(AS) $(AFLAGS) $<|ml $<|No|x86|
|.asm.obj|$(AS) $(AFLAGS) /c $<|ml /c $<|sí|x86|
|.asm.exe|$(AS) $(AFLAGS) $<|ml64 $<|No|x64|
|.asm.obj|$(AS) $(AFLAGS) /c $<|ml64 /c $<|sí|x64|
|.c.exe|$(CC) $(CFLAGS) $<|cl $<|no|todo|
|.c.obj|$(CC) $(CFLAGS) /c $<|cl /c $<|sí|todo|
|.cc.exe|$(CC) $(CFLAGS) $<|cl $<|no|todo|
|.cc.obj|$(CC) $(CFLAGS) /c $<|cl /c $<|sí|todo|
|.cpp.exe|$(CPP) $(CPPFLAGS) $<|cl $<|no|todo|
|.cpp.obj|$(CPP) $(CPPFLAGS) /c $<|cl /c $<|sí|todo|
|.cxx.exe|$(CXX) $(CXXFLAGS) $<|cl $<|no|todo|
|.cxx.obj|$(CXX) $(CXXFLAGS) /c $<|cl /c $<|sí|todo|
|.rc.res|$(RC) $(RFLAGS) /r $<|rc /r $<|No|todo|

## <a name="see-also"></a>Vea también

[Reglas de inferencia](../build/inference-rules.md)