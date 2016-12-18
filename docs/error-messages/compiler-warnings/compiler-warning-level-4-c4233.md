---
title: "Advertencia del compilador (nivel 4) C4233 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4233"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4233"
ms.assetid: 9aa51fc6-8ef3-43b5-bafb-c9333cf60de3
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 4) C4233
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

se ha utilizado una extensión no estándar : la palabra clave 'palabraclave' sólo se admite en C\+\+, no en C  
  
 El compilador compiló el código fuente como C en lugar de C\+\+, y se utilizó una palabra clave que sólo es válida en C\+\+.  El compilador compila el código fuente como C si la extensión del archivo de código es .c o se utiliza [\/Tc](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md).  
  
 Esta advertencia suele convertirse automáticamente en un error.  Si desea modificar este comportamiento, use [\#pragma warning](../../preprocessor/warning.md).  Por ejemplo, para convertir C4233 en una advertencia de nivel 4:  
  
```  
#pragma warning(2:4233)  
```  
  
 en el archivo de código fuente.