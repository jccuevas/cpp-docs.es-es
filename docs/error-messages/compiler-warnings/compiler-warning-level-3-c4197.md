---
title: Compilador advertencia (nivel 3) C4197 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4197
dev_langs:
- C++
helpviewer_keywords:
- C4197
ms.assetid: f766feef-82b0-4d81-8a65-33628c7db196
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fa119e0b1afd3f660dd04040965006f1b52cad01
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33290431"
---
# <a name="compiler-warning-level-3-c4197"></a>Compilador C4197 de advertencia (nivel 3)
'type': se omite volatile de nivel superior en la conversión  
  
 El compilador detectó una conversión a un tipo de valor r que se califica con [volátiles](../../cpp/volatile-cpp.md), o una conversión de un tipo de valor r como un tipo que se califica mediante volatile. Según el estándar de C (6.5.3), propiedades asociadas a tipos calificados tienen sentidos sólo para expresiones de valor l.  
  
 El ejemplo siguiente genera C4197:  
  
```  
// C4197.cpp  
// compile with: /W3  
#include <stdio.h>  
#include <signal.h>  
#include <stdlib.h>  
  
void sigproc(int);  
struct S  
{  
   int i;  
} s;  
  
int main()  
{  
   signal(SIGINT, sigproc);  
   s.i = 1;  
   S *pS = &s;  
   for ( ; (volatile int)pS->i ; )   // C4197  
      break;  
   // for ( ; *(volatile int *)&pS->i ; )   // OK  
   //    break;  
}  
  
void sigproc(int) // ctrl-C  
{  
   signal(SIGINT, sigproc);  
   s.i = 0;  
}  
  
```