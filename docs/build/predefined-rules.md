---
title: "Reglas predefinidas | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "reglas, predefinidas"
  - "NMAKE (programa), reglas predefinidas"
  - "reglas predefinidas en NMAKE"
ms.assetid: 638cdc3f-4aba-4b4f-96e3-ad65b0364f12
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Reglas predefinidas
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las reglas de inferencia predefinidas utilizan macros de comando y de opciones proporcionadas por NMAKE.  
  
|Regla|Command|Valor<br /><br /> predeterminada|por lotes<br /><br /> Regla|Plataforma donde se ejecuta NMAKE|  
|-----------|-------------|------------------------------|-------------------------|---------------------------------------|  
|.asm.exe|$\(AS\) $\(AFLAGS\) $\<|ml $\<|no|x86|  
|.asm.obj|$\(AS\) $\(AFLAGS\) \/c $\<|ml \/c $\<|sí|x86|  
|.asm.exe|$\(AS\) $\(AFLAGS\) $\<|ml64 $\<|no|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|.asm.obj|$\(AS\) $\(AFLAGS\) \/c $\<|ml64 \/c $\<|sí|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|.c.exe|$\(CC\) $\(CFLAGS\) $\<|cl $\<|no|todas|  
|.c.obj|$\(CC\) $\(CFLAGS\) \/c $\<|cl \/c $\<|sí|todas|  
|.cc.exe|$\(CC\) $\(CFLAGS\) $\<|cl $\<|no|todas|  
|.cc.obj|$\(CC\) $\(CFLAGS\) \/c $\<|cl \/c $\<|sí|todas|  
|.cpp.exe|$\(CPP\) $\(CPPFLAGS\) $\<|cl $\<|no|todas|  
|.cpp.obj|$\(CPP\) $\(CPPFLAGS\) \/c $\<|cl \/c $\<|sí|todas|  
|.cxx.exe|$\(CXX\) $\(CXXFLAGS\) $\<|cl $\<|no|todas|  
|.cxx.obj|$\(CXX\) $\(CXXFLAGS\) \/c $\<|cl \/c $\<|sí|todas|  
|.rc.res|$\(RC\) $\(RFLAGS\) \/r $\<|rc \/r $\<|no|todas|  
  
## Vea también  
 [Reglas de inferencia](../build/inference-rules.md)