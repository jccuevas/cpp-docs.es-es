---
title: Error del compilador C3855 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3855
dev_langs: C++
helpviewer_keywords: C3855
ms.assetid: ed90f8c0-4154-4243-b066-493913df5727
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 76d9101fd58d419db227803d3964198523ce3630
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3855"></a>Error del compilador C3855
'clase': parámetro de tipo 'param' no es compatible con la declaración  
  
 El compilador encontró parámetros genéricos con nombres diferentes o plantilla sin tipo. Esto puede ocurrir cuando un parámetro de plantilla especificado en la definición de una especialización de plantilla es incompatible con su declaración.  
  
 El ejemplo siguiente genera C3855:  
  
```  
// C3855.cpp  
template <int N>  
struct C {  
   void f();  
};  
  
template <char N>  
void C<N>::f() {}   // C3855  
```  
  
 Posible solución:  
  
```  
// C3855b.cpp  
// compile with: /c  
template <int N>  
struct C {  
   void f();  
};  
  
template <int N>  
void C<N>::f() {}  
```  
  
 C3855 también puede producirse al usar genéricos:  
  
```  
// C3855c.cpp  
// compile with: /clr  
generic <class T>  
ref struct GC1 {  
   generic <class U>  
   ref struct GC2;  
};  
  
generic <class T>  
generic <class U>  
generic <class V>  
ref struct GC1<T>::GC2 { };   // C3855  
```  
  
 Posible solución:  
  
```  
// C3855d.cpp  
// compile with: /clr /c  
generic <class T>  
ref struct GC1 {  
   generic <class U>  
   ref struct GC2;  
};  
  
generic <class T>  
generic <class U>  
ref struct GC1<T>::GC2 { };  
```