---
title: Error del compilador C3230 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3230
dev_langs:
- C++
helpviewer_keywords:
- C3230
ms.assetid: 5ec53f25-59f6-4801-81e7-7b68bf04994d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 494aa6a04b1ec4844e243807e103d4d106380739
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33252417"
---
# <a name="compiler-error-c3230"></a>Error del compilador C3230
'función': el argumento de tipo de plantilla para 'plantilla' no puede contener un parámetro de tipo genérico: 'parámetro'  
  
 Las instancias de las plantillas se crean en tiempo de compilación, mientras que las instancias de los genéricos se crean en tiempo de ejecución. Por consiguiente, no es posible generar código genérico que pueda llamar a la plantilla, porque no se pueden crear instancias de la plantilla en tiempo de ejecución si finalmente se conoce el tipo genérico.  
  
 El ejemplo siguiente genera la advertencia C3230:  
  
```  
// C3230.cpp  
// compile with: /clr /LD  
template <class S>   
void f(S t);  
  
generic <class U>  
ref class C {  
   void f1(U x) {  
      f(x);   // C3230  
   }  
};  
```