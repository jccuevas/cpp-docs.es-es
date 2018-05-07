---
title: Error del compilador C2534 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2534
dev_langs:
- C++
helpviewer_keywords:
- C2534
ms.assetid: 481f9f54-5b51-4aa0-8eea-218f10807705
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bae52374e09852ffb68c5807353155d9928924eb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2534"></a>Error del compilador C2534
'identificador': constructor no puede devolver un valor  
  
 Un constructor no puede devolver un valor o tener un tipo de valor devuelto (ni siquiera un `void` tipo de valor devuelto).  
  
 Este error puede corregirse quitando el `return` instrucción desde la definición del constructor.  
  
 El ejemplo siguiente genera C2534:  
  
```  
// C2534.cpp  
class A {  
public:  
   int i;  
   A() { return i; }   // C2534  
};  
```