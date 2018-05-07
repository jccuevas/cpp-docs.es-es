---
title: Error de compilador Error C3195 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3195
dev_langs:
- C++
helpviewer_keywords:
- C3195
ms.assetid: 97e4f681-812b-49e8-ba57-24b7817e3cd8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6ce3c51da68b971c34d651826a9c84974957ac46
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3195"></a>Error C3195 de Error del compilador
'operador' : está reservado y no se puede utilizar como miembro de una clase ref o de un tipo de valor. Los operadores CLR o WinRT se deben definir mediante la palabra clave 'operator'  
  
El compilador detectó una definición de operador con la sintaxis de Extensiones administradas para C++. Debe usar la sintaxis de C++ para los operadores.  
  
El ejemplo siguiente genera el error C3195 y muestra cómo corregirlo:  
  
```  
// C3195.cpp  
// compile with: /clr /LD  
#using <mscorlib.dll>  
value struct V {  
   static V op_Addition(V v, int i);   // C3195  
   static V operator +(V v, char c);   // OK for new C++ syntax   
};  
```