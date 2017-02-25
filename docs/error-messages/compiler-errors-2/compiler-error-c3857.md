---
title: "Error del compilador C3857 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3857"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3857"
ms.assetid: 9f746d1e-9708-4945-bc29-3150d5371d3c
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Error del compilador C3857
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'tipo' : no se permiten listas de parámetros de tipos múltiples  
  
 Se ha especificado más de una plantilla o genérico para el mismo tipo, lo que no está permitido.  
  
 El código siguiente genera el error C3857:  
  
```  
// C3857.cpp  
template <class T, class TT>  
template <class T2>    // C3857  
struct B {};  
```  
  
 Posible solución:  
  
```  
// C3857b.cpp  
// compile with: /c  
template <class T, class TT, class T2>   
struct B {};  
```  
  
 El error C3857 también puede producirse cuando se usan genéricos:  
  
```  
// C3857c.cpp  
// compile with: /clr  
generic <typename T>  
generic <typename U>  
ref class GC;   // C3857  
```  
  
 Posible solución:  
  
```  
// C3857d.cpp  
// compile with: /clr /c  
generic <typename U>  
ref class GC;  
```