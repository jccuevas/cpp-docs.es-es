---
title: Compilador advertencia (nivel 2) C4244 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4244
dev_langs:
- C++
helpviewer_keywords:
- C4244
ms.assetid: 2c19d157-21d1-42c2-a6c0-3f30f2ce3813
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: de3b2392575f069c9ffc7b661cbd647f81f9557b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33290717"
---
# <a name="compiler-warning-level-2-c4244"></a>Advertencia del compilador (nivel 2) C4244
'argument': conversión de 'tipo1' a 'tipo2', posible pérdida de datos  
  
 Un tipo de punto flotante se convierte en un tipo entero.  Se ha producido una posible pérdida de datos.  
  
 Si recibe el error C4244, debe cambiar el programa para que use tipos compatibles o agregar lógica al código, para asegurarse de que el intervalo de valores posibles sea siempre compatible con los tipos que usa.  
  
 C4244 también puede producirse en el nivel 3 y 4; vea [advertencia del compilador (niveles 3 y 4) C4244](../../error-messages/compiler-warnings/compiler-warning-levels-3-and-4-c4244.md) para obtener más información.  
  
## <a name="example"></a>Ejemplo  
 El siguiente ejemplo genera C4244:  
  
```  
// C4244_level2.cpp  
// compile with: /W2  
  
int f(int x){ return 0; }  
int main() {  
   double x = 10.1;  
   int i = 10;  
   return (f(x));   // C4244  
   // try the following line instead  
   // return (f(i));  
}  
```