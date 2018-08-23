---
title: Reglas predefinidas | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- rules, predefined
- NMAKE program, predefined rules
- predefined rules in NMAKE
ms.assetid: 638cdc3f-4aba-4b4f-96e3-ad65b0364f12
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 52c9440a0320bbc59e5d2552a53e13fae5e29f05
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/14/2018
ms.locfileid: "42572213"
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