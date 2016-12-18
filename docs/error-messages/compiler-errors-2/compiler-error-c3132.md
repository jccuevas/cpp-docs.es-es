---
title: "Error del compilador C3132 | Microsoft Docs"
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
  - "C3132"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3132"
ms.assetid: d54a3d12-336a-4ed0-ad4e-43cddac33b5e
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3132
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'parámetro de función': las matrices de parámetros sólo se pueden aplicar a un argumento formal de tipo 'matriz administrada unidimensional'  
  
 Se ha aplicado el atributo [ParamArray](https://msdn.microsoft.com/en-us/library/system.paramarrayattribute.aspx) a un parámetro que no era una matriz unidimensional.  
  
 El código siguiente genera el error C3132:  
  
```  
// C3132.cpp  
// compile with: /clr /c  
using namespace System;  
void f( [ParamArray] Int32[,] );   // C3132  
void g( [ParamArray] Int32[] );   // C3132  
  
void h( [ParamArray] array<Char ^> ^ MyArray );   // OK  
  
```