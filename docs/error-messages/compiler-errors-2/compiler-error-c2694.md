---
title: C2694 de Error del compilador | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2694
dev_langs:
- C++
helpviewer_keywords:
- C2694
ms.assetid: 8dc2cec2-67ae-4e16-8c0c-374425aca8bc
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7a979cf038af6cb4300519a2eae735e94e84c53a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2694"></a>C2694 de Error del compilador
'override': función virtual de reemplazo tiene una especificación de excepción menos restrictiva que la clase base miembro virtual función 'base'  
  
 Se ha reemplazado una función virtual, pero en [/Za](../../build/reference/za-ze-disable-language-extensions.md), el reemplazo de la función tenía una menos restrictiva [una especificación de excepción](../../cpp/exception-specifications-throw-cpp.md).  
  
 El ejemplo siguiente genera C2694:  
  
```  
// C2694.cpp  
// compile with: /Za /c  
class MyBase {  
public:  
   virtual void f(void) throw(int) {  
   }  
};  
  
class Derived : public MyBase {  
public:  
   void f(void) throw(...) {}   // C2694  
   void f2(void) throw(int) {}   // OK  
};  
```