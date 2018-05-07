---
title: Compilador advertencia (nivel 4) C4213 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4213
dev_langs:
- C++
helpviewer_keywords:
- C4213
ms.assetid: 59fc3f61-ebd2-499e-99d7-f57bec11eda1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 407fac636ea33c8cbd31104460442e5ac2aaec65
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4213"></a>Advertencia del compilador (nivel 4) C4213
ha utilizado una extensión no estándar: conversión de valor l  
  
 Con las extensiones de Microsoft (/Ze) de manera predeterminada, puede usar conversiones de tipos en el lado izquierdo de una instrucción de asignación.  
  
## <a name="example"></a>Ejemplo  
  
```  
// C4213.c  
// compile with: /W4  
void *a;  
void f()  
{  
   int   i[3];  
   a = &i;  
   *(( int * )a )++ = 3;  // C4213  
}  
  
int main()  
{  
}  
```  
  
 Tales conversiones no son válidas en la compatibilidad con ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).