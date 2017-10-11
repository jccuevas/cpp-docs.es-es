---
title: Error de compilador Error C3195 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3195
dev_langs:
- C++
helpviewer_keywords:
- C3195
ms.assetid: 97e4f681-812b-49e8-ba57-24b7817e3cd8
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: e6e95ce1592c98fae59869e0153ee27c0f727397
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

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
