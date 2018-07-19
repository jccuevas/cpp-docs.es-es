---
title: Reglas predefinidas | Documentos de Microsoft
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
ms.openlocfilehash: d0a21847bb9363099fa64825b45a90003de053da
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32369765"
---
# <a name="predefined-rules"></a>Reglas predefinidas
Las reglas de inferencia predefinidas utilizan macros de comando y de opciones proporcionadas por NMAKE.  
  
|Regla|Comando|Default<br /><br /> predeterminada|por lotes<br /><br /> Regla|Plataforma donde se ejecuta NMAKE|  
|----------|-------------|------------------------|--------------------|----------------------------|  
|.asm.exe|$(AS) $(AFLAGS) $<|ml $<|No|x86|  
|.asm.obj|$(AS) $(AFLAGS) /c $<|ml /c $<|sí|x86|  
|.asm.exe|$(AS) $(AFLAGS) $<|ml64 $<|No|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|.asm.obj|$(AS) $(AFLAGS) /c $<|ml64 /c $<|sí|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
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