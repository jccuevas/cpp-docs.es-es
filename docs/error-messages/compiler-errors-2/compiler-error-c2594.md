---
title: Error del compilador C2594 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2594
dev_langs:
- C++
helpviewer_keywords:
- C2594
ms.assetid: 68cd708f-266e-44b0-a211-3e3ab63b11bf
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: a6a73e5202b90a0bc436d93be142162531c6d204
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2594"></a>Error del compilador C2594
'operador': conversiones ambiguas de 'tipo1' a 'tipo2'  
  
 Ninguna conversión de *type1* a *type2* es más directa que cualquier otro. Sugerimos dos posibles soluciones para convertir de *type1* a *type2*. La primera opción consiste en definir una conversión directa de *type1* a *type2*, y la segunda opción consiste en especificar una secuencia de conversiones de *type1* a  *type2*.  
  
 El ejemplo siguiente genera C2594. La solución sugerida para el error es una secuencia de conversiones:  
  
```  
// C2594.cpp  
// compile with: /c  
struct A{};  
struct I1 : A {};  
struct I2 : A {};  
struct D : I1, I2 {};  
  
A *f (D *p) {  
   return (A*) (p);    // C2594  
  
// try the following line instead  
// return static_cast<A *>(static_cast<I1 *>(p));  
}  
```
