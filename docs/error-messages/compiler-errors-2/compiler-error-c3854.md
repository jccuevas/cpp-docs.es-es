---
title: Error del compilador C3854 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3854
dev_langs:
- C++
helpviewer_keywords:
- C3854
ms.assetid: 32a9ead0-c6c7-485a-8802-c7b1fe921d3a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dbaed18984dbcc06b976a367ef9911528792ce52
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33275517"
---
# <a name="compiler-error-c3854"></a>Error del compilador C3854
expresión a la izquierda de '=' se evalúa como una función. No se puede asignar a una función (una función no es un valor l)  
  
 No se puede reinicializar una referencia. Desreferenciar una referencia a una función produce una función, que es un valor r, al que no se puede asignar. Por lo tanto, no se puede asignar mediante una referencia a una función.  
  
 El ejemplo siguiente genera C3854:  
  
```  
// C3854.cpp  
int afunc(int i)  
{  
   return i;  
}  
  
typedef int (& rFunc_t)(int);  
typedef int (* pFunc_t)(int);  
  
int main()  
{  
   rFunc_t rf = afunc;   // OK binding a reference to function  
   pFunc_t pf = &afunc;   // OK initializing a pointer to function  
  
   *pf = &afunc;   // C3854  
   // try the following line instead  
   // pf = &afunc;  
   *rf = &afunc;   // C3854  
}  
```