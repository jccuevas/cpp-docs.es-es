---
title: Error del compilador C3264 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3264
dev_langs:
- C++
helpviewer_keywords:
- C3264
ms.assetid: 94ece687-2364-4f7a-8ebb-7afd3ae9d63d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6404b2b83381bc29283232b9d2587bef7cb27bb9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33252502"
---
# <a name="compiler-error-c3264"></a>Error del compilador C3264
'clase': un constructor de clase no puede tener un tipo de valor devuelto.  
  
Los constructores de clase no pueden tener tipos de valor devueltos.  
  
El ejemplo siguiente genera la advertencia C3264:  
  
```  
// C3264_2.cpp  
// compile with: /clr  
  
ref class X {  
   public:  
      static int X()   { // C3264  
      }  
  
      /* use the code below to resolve the error  
      static X() {  
      }  
      */  
};  
int main() {  
}  
```  
