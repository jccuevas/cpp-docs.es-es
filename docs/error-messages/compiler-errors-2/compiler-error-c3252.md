---
title: Error del compilador C3252 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3252
dev_langs:
- C++
helpviewer_keywords:
- C3252
ms.assetid: aa9ad096-e9ac-41c7-8ad9-b966751c7c75
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4bc7ca0ccf3c973363e4427c89ccf497c20d1791
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3252"></a>Error del compilador C3252
'método': no se puede reducir la accesibilidad de un método virtual en un tipo administrado o WinRT  
  
 Una clase que implementa un método virtual de una clase base o cualquier método de una interfaz no puede reducir el acceso a ese método.  
  
 Tenga en cuenta que todos los métodos de una interfaz son públicos.  
  
 En el ejemplo siguiente se genera el error C3252 y se muestra cómo corregirlo.  
  
```  
// C3252.cpp  
// compile with: /clr /c  
ref class A {  
public:  
   virtual void f1() {}  
};  
  
ref class B : public A {  
// To fix, uncomment the following line:   
// public:      
   virtual void f1() override sealed {}   // C3252, make this method public  
};  
```