---
title: Reglas predefinidas | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- rules, predefined
- NMAKE program, predefined rules
- predefined rules in NMAKE
ms.assetid: 638cdc3f-4aba-4b4f-96e3-ad65b0364f12
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3be1c8eea7b11f60e9ce9a7cbf5ebc0c2b99b698
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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