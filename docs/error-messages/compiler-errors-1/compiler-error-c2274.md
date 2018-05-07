---
title: Error del compilador C2274 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2274
dev_langs:
- C++
helpviewer_keywords:
- C2274
ms.assetid: 8e874903-f499-45ef-8291-f821eee4cc1c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dfd9bda3f3b0ab267ec008443dd865334e1b765e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2274"></a>Error del compilador C2274
'type': no es válido como lado derecho de '.' operador  
  
 Aparece un tipo como operando derecho de un operador de acceso a miembros (.).  
  
 Este error puede deberse a intentar obtener acceso a una conversión de tipo definido por el usuario. Use la palabra clave `operator` entre el período y `type`.  
  
 El ejemplo siguiente genera la advertencia C2286:  
  
```  
// C2274.cpp  
struct MyClass {  
   operator int() {  
      return 0;  
   }  
};  
  
int main() {  
   MyClass ClassName;  
   int i = ClassName.int();   // C2274  
   int j = ClassName.operator int();   // OK  
}  
```