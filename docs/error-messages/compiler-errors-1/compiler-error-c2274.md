---
title: Error del compilador C2274 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2274
dev_langs:
- C++
helpviewer_keywords:
- C2274
ms.assetid: 8e874903-f499-45ef-8291-f821eee4cc1c
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 4315d1cfef9a0583b1f44c8caa264378e32f1a35
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

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
