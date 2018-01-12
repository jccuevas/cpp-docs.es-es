---
title: Error del compilador C3856 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3856
dev_langs: C++
helpviewer_keywords: C3856
ms.assetid: 242d9322-c325-4f20-be58-b2be6da56d60
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ba0be4ea7cf7d82ce8c0ee412f8373ea14f1162e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3856"></a>Error del compilador C3856
'type': no es un tipo de clase  
  
 La causa más común de este error es cuando hay más genérica o listas de parámetros de plantilla en el punto de definición que había en el punto de declaración.  
  
 El ejemplo siguiente genera C3856:  
  
```  
// C3856.cpp  
template <class T>   
struct S {  
   template <class T1>   
   struct S1;   
   void f();   
};  
  
template <class T>   // C3856  
template <class T1>  
template <class T2>  // extra template parameter list in definition  
struct S<T>::S1{};  
```  
  
 Posible resolución:  
  
```  
// C3856b.cpp  
// compile with: /c  
template <class T>   
struct S {  
   template <class T1>   
   struct S1;   
   void f();   
};  
  
template <class T>  
template <class T1>  
struct S<T>::S1{};  
```  
  
 C3856 también puede producirse al usar genéricos:  
  
```  
// C3856c.cpp  
// compile with: /clr  
generic <class T>  
ref struct GS {  
   generic <class U>  
   ref struct GS2;  
};  
  
generic <class T>  
generic <class U>  
generic <class V>  
ref struct GS<T>::GS2 {};   // C3856  
```  
  
 Posible resolución:  
  
```  
// C3856d.cpp  
// compile with: /clr /c  
generic <class T>  
ref struct GS {  
   generic <class U>  
   ref struct GS2;  
};  
  
generic <class T>  
generic <class U>  
ref struct GS<T>::GS2 {};  
```