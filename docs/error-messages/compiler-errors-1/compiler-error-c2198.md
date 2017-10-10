---
title: Error del compilador C2198 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2198
dev_langs:
- C++
helpviewer_keywords:
- C2198
ms.assetid: 638a845c-9d7f-4115-a9aa-d72455605668
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 0da955515b5ad51836a82563fcfdf8d70de14470
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2198"></a>Error del compilador C2198
'function': no hay suficientes argumentos para la llamada  
  
 El compilador no encontró parámetros suficientes para realizar una llamada a la función o detectó una declaración de función incorrecta.  
  
 El ejemplo siguiente genera la advertencia C2198:  
  
```  
// C2198.c  
// compile with: /c  
void func( int, int );  
int main() {  
   func( 1 );   // C2198 only one actual parameter  
   func( 1, 1 );   // OK  
}  
```
