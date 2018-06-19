---
title: Error del compilador C2563 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2563
dev_langs:
- C++
helpviewer_keywords:
- C2563
ms.assetid: 54abba68-6458-4ca5-894d-3babdb7b3552
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 85a4de195c681ce8d11b789a9aca102629cc2bac
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33228602"
---
# <a name="compiler-error-c2563"></a>Error del compilador C2563
Error de coincidencia en la lista de parámetros formales  
  
 La lista de parámetros formales de una función (o un puntero a una función) no coincide con los de otra función (o puntero a una función miembro). Como resultado, no se puede realizar la asignación de funciones o punteros.  
  
 El ejemplo siguiente genera C2563:  
  
```  
// C2563.cpp  
void func( int );  
void func( int, int );  
int main() {  
   void *fp();  
   fp = func;   // C2563  
}  
```