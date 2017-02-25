---
title: "Error del compilador C2632 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2632"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2632"
ms.assetid: b15a6b1b-42d2-4e1b-8660-e6bfde61052d
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# Error del compilador C2632
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'tipo1' seguido de 'tipo2' no es válido  
  
 Se puede producir este error si falta código entre dos especificadores de tipo.  
  
 El código siguiente genera el error C2632:  
  
```  
// C2632.cpp  
int float i;   // C2632  
```  
  
 Este error también puede producirse como resultado del trabajo de conformidad del compilador realizado para Visual Studio .NET 2003.  `bool` es ahora un tipo apropiado.  En versiones anteriores, `bool` era una definición de tipos y se podían crear los identificadores con ese nombre.  
  
 El código siguiente genera el error C2632:  
  
```  
// C2632_2.cpp  
// compile with: /LD  
void f(int bool);   // C2632  
```  
  
 Para corregir este error de forma que el código sea válido en las versiones de Visual Studio .NET 2003 y Visual Studio .NET de Visual C\+\+, cambie el nombre del identificador.