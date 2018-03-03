---
title: Compilador advertencia (nivel 1) C4807 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4807
dev_langs:
- C++
helpviewer_keywords:
- C4807
ms.assetid: 089c9f87-fd81-402e-9826-66a8ef1ef1fe
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: af604a1a045b9dbef7b3c27f9c7aabd0040aa318
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4807"></a>Advertencia del compilador (nivel 1) C4807
'operation': combinación no segura del tipo 'type' y el campo de bits con signo de tipo 'type'  
  
 Esta advertencia se genera al comparar un campo de bits con signo de un bit con una variable `bool` . Puesto que el campo de bits con signo de un bit solo puede contener los valores -1 o 0, es arriesgado compararlo con `bool`. No se generan advertencias con la mezcla de `bool` y campos de bits sin signo de un bit, ya que son idénticas a `bool` y solo pueden contener 0 o 1.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera la advertencia C4807:  
  
```  
// C4807.cpp  
// compile with: /W1  
typedef struct bitfield {  
   signed mybit : 1;  
} mybitfield;  
  
int main() {  
   mybitfield bf;  
   bool b = true;  
  
   // try..  
   // int b = true;  
  
   bf.mybit = -1;  
   if (b == bf.mybit) {   // C4807  
      b = false;  
   }  
}  
```