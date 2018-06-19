---
title: Error del compilador C2883 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2883
dev_langs:
- C++
helpviewer_keywords:
- C2883
ms.assetid: 5c6d689d-ed42-41ad-b5c0-e9c2e0b8c356
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fc3119db27127521f5078a5753bb82c82da381ed
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33244952"
---
# <a name="compiler-error-c2883"></a>Error del compilador C2883
'name': declaración de función entra en conflicto con 'identificador' introducido por la declaración using  
  
 Se intentó definir una función de más de una vez. Se realizó la primera definición de un espacio de nombres con un `using` declaración. La segunda era una definición local.  
  
 El ejemplo siguiente genera C2883:  
  
```  
// C2883.cpp  
namespace A {  
   void z(int);  
}  
  
int main() {  
   using A::z;  
   void z(int);   // C2883  z is already defined  
}  
```