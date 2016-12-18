---
title: "Error irrecuperable C1383 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C1383"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1383"
ms.assetid: ca224d14-d687-4fd6-80c2-8b82f28924ea
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error irrecuperable C1383
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

la opción \/GL del compilador es incompatible con la versión instalada de Common Language Runtime  
  
 El error C1383 se genera si utiliza una versión anterior de Common Language Runtime con un compilador más reciente y cuando se compila con **\/clr** y **\/GL.**  
  
 Para solucionarlo, no utilice **\/GL** con **\/clr** o instale la versión de Common Language Runtime que se distribuía con su compilador.  
  
 Para obtener más información, consulte [\/clr \(Compilación de Common Language Runtime\)](../../build/reference/clr-common-language-runtime-compilation.md) y [\/GL \(Optimización de todo el programa\)](../../build/reference/gl-whole-program-optimization.md).