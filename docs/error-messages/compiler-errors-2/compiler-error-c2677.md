---
title: C2677 de Error del compilador | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2677
dev_langs:
- C++
helpviewer_keywords:
- C2677
ms.assetid: 76bc0b65-f52a-45a6-b6d6-0555f89da9a8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 671be6d7e6acf252b774c4cd379fbc15267e4d94
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2677"></a>C2677 de Error del compilador
'operador' binario: ningún operador global encontró que adopte el tipo 'type' (o no hay ninguna conversión aceptable)  
  
 Para usar este operador, debe sobrecargarlo para el tipo especificado o definir una conversión a un tipo para el que esté definido el operador.  
  
 El ejemplo siguiente genera C2677:  
  
```  
// C2677.cpp  
class C {  
public:  
   C(){}  
} c;  
  
class D {  
public:  
   D(){}  
   operator int(){return 0;}  
} d;  
  
int main() {  
   int i = 1 >> c;   // C2677  
   int j = 1 >> d;   // OK operator int() defined  
}  
```