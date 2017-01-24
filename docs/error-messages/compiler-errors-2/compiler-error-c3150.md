---
title: "Error del compilador C3150 | Microsoft Docs"
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
  - "C3150"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3150"
ms.assetid: c1ff28f5-52fe-4fd4-81d0-2e0ad8548631
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3150
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'elemento' : 'atributo' sólo se puede aplicar a una clase, interfaz, matriz o puntero  
  
 [Sólo se puede utilizar \_\_gc](../../misc/gc.md) en una clase, interfaz o matriz.  
  
 Sólo se puede reproducir el error C3150 utilizando **\/clr:oldSyntax**.  
  
 El código siguiente genera el error C3150:  
  
```  
// C3150.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
  
__gc void f()   // C3150; function cannot be managed  
{  
}  
```