---
title: "Error del compilador C3747 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3747"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3747"
ms.assetid: a9a4be67-5d9c-4dcc-9ae9-baae46cbecde
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error del compilador C3747
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

falta el parámetro de tipo predeterminado : parámetro param  
  
 Los parámetros genéricos o de plantilla con valores predeterminados no pueden ir seguidos en la lista de parámetros por parámetros que no posean también valores predeterminados.  
  
 El código siguiente genera el error C3747:  
  
```  
// C3747.cpp  
template <class T1 = int, class T2>   // C3747  
struct MyStruct {};  
```  
  
 Posible solución:  
  
```  
// C3747b.cpp  
// compile with: /c  
template <class T1, class T2 = int>  
struct MyStruct {};  
```