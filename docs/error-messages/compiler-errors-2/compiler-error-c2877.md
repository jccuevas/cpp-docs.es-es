---
title: Error del compilador C2877 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2877
dev_langs:
- C++
helpviewer_keywords:
- C2877
ms.assetid: 0b54837e-fcae-4d90-9658-623250435e24
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 96ab91d64806e7d4ca28bf43e812640790b78e87
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33245017"
---
# <a name="compiler-error-c2877"></a>Error del compilador C2877
'símbolo' no es accesible desde 'clase'  
  
 Todos los miembros que se deriva de una clase base deben ser accesibles en la clase derivada.  
  
 El ejemplo siguiente genera C2877:  
  
```  
// C2877.cpp  
// compile with: /c  
class A {  
private:  
   int a;  
};  
  
class B : public A {  
   using A::a;   // C2877  
};  
```