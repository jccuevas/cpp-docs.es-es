---
title: Compilador advertencia (nivel 3) C4265 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4265
dev_langs:
- C++
helpviewer_keywords:
- C4265
ms.assetid: 20547159-6f30-4cc4-83aa-927884c8bb4c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 587f4b09718fbd8f8debf0c85178feb9f9616a6d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-3-c4265"></a>Advertencia del compilador (nivel 3) C4265
'clase': clase tiene funciones virtuales, pero el destructor no es virtual  
  
 Cuando una clase tiene funciones virtuales pero un destructor no virtual, objetos del tipo podrían no se destruyen correctamente cuando se destruye la clase a través de un puntero de clase base.  
  
 De forma predeterminada, esta advertencia está desactivada. Vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md) para más información.  
  
 El ejemplo siguiente genera C4265:  
  
```  
// C4265.cpp  
// compile with: /W3 /c  
#pragma warning(default : 4265)  
class B  
{  
public:  
   virtual void vmf();  
  
   ~B();  
   // try the following line instead  
   // virtual ~B();  
};   // C4265  
  
int main()  
{  
   B b;  
}  
```