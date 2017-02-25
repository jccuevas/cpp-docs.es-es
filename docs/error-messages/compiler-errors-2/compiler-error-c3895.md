---
title: "Error del compilador C3895 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3895"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3895"
ms.assetid: 771b9fe5-d6d4-4297-bf57-e2f857722155
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Error del compilador C3895
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'var' : los miembros de datos de tipo no pueden ser 'volatile'  
  
 Algunos tipos de miembros de datos, por ejemplo [literal](../../windows/literal-cpp-component-extensions.md) o [initonly](../../dotnet/initonly-cpp-cli.md), no pueden ser [volatile](../../cpp/volatile-cpp.md).  
  
 El código siguiente genera el error C3895:  
  
```  
// C3895.cpp  
// compile with: /clr  
ref struct Y1 {  
   initonly  
   volatile int data_var2;   // C3895  
};  
```