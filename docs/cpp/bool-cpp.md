---
title: "bool (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "bool_cpp"
  - "bool"
  - "__BOOL_DEFINED"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__BOOL_DEFINED (macro)"
  - "bool (palabra clave) [C++]"
ms.assetid: 9abed3f2-d21c-4eb4-97c5-716342e613d8
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# bool (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Esta palabra clave es un tipo integrado.  Una variable de este tipo puede tener valores [true](../cpp/true-cpp.md) y [false](../cpp/false-cpp.md).  Las expresiones condicionales tienen el tipo `bool` y, por lo tanto, tienen valores de tipo `bool`.  Por ejemplo, `i!=0` ahora tiene **true** o **false** dependiendo del valor de `i`.  
  
 Los valores **true** y **false** tienen la relación siguiente:  
  
```  
!false == true  
!true == false  
```  
  
 En la instrucción siguiente:  
  
```  
if (condexpr1) statement1;   
```  
  
 Si `condexpr1` es **true**, `statement1` siempre se ejecuta; si `condexpr1` es **false**, `statement1` nunca se ejecuta.  
  
 Cuando se aplica un operador `++` de prefijo o de postfijo a una variable de tipo `bool`, la variable se establece en **true**.  El operador `--` de prefijo o de postfijo no se puede aplicar a una variable de este tipo.  
  
 El tipo `bool` participa en promociones enteras.  Un valor R de tipo `bool` se puede convertir en un valor R de tipo `int`, con **false** como cero y **true** como uno.  Como un tipo distinto, `bool` participa en la resolución de sobrecarga.  
  
## Vea también  
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)   
 [Tipos fundamentales](../cpp/fundamental-types-cpp.md)