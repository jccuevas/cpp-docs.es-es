---
title: "Advertencia del compilador (nivel 1) C4627 | Microsoft Docs"
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
  - "C4627"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4627"
ms.assetid: 8840f3e6-b496-423a-8635-eb55d5f854a2
caps.latest.revision: 3
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4627
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'\<identificador\>': se omite al buscar el uso del encabezado precompilado.  
  
 Al buscar la ubicación donde se usa un encabezado precompilado, el compilador encontró una directiva `#include` para el archivo de inclusión *\<identificador\>*. El compilador omite la directiva `#include`, pero emite la advertencia **C4627** si el encabezado precompilado aún no contiene el archivo de inclusión *\<identificador\>*.  
  
## Vea también  
 [Crear archivos de encabezado precompilados](../../build/reference/creating-precompiled-header-files.md)