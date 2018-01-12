---
title: Error del compilador C2594 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2594
dev_langs: C++
helpviewer_keywords: C2594
ms.assetid: 68cd708f-266e-44b0-a211-3e3ab63b11bf
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d4cca18672aad77e051ff4428dc115c53cd5ddad
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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