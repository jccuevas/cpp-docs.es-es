---
title: C2679 de Error del compilador | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2679
dev_langs:
- C++
helpviewer_keywords:
- C2679
ms.assetid: 1a5f9d00-9190-4aa6-bc72-949f68ec136f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 24a304d88ccc6044c5358759efffa2a38dfeaf67
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2679"></a>C2679 de Error del compilador
'operador' binario: no encontró ningún operador que adopte un operando derecho del tipo 'type' (o no hay ninguna conversión aceptable)  
  
 Para usar este operador, debe sobrecargarlo para el tipo especificado o definir una conversión a un tipo para el que esté definido el operador.  
  
 El ejemplo siguiente genera C2679:  
  
```  
// C2679.cpp  
class C {  
public:  
   C();   // no constructor with an int argument  
} c;  
  
class D {  
public:  
   D(int) {}  
   D(){}  
} d;  
  
int main() {  
   c = 10;   // C2679  
   d = 10;   // OK  
}  
```