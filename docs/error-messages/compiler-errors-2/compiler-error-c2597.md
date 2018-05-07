---
title: Error del compilador C2597 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2597
dev_langs:
- C++
helpviewer_keywords:
- C2597
ms.assetid: 2e48127d-e3ff-4a40-8156-2863e45b1a38
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 45cf9054736117526ee5e79c0bafdd8fdee7c2e2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2597"></a>Error del compilador C2597
referencia no válida a miembro no estático 'identifier'  
  
 Causas posibles:  
  
1.  Se especifica un miembro no estático en una función de miembro estático. Para tener acceso al miembro no estático, debe pasar o crear una instancia local de la clase y usar un operador de acceso a miembros (`.` o `->`).  
  
2.  El identificador especificado no es miembro de una clase, estructura o unión. Revisar la ortografía del identificador.  
  
3.  Un operador de acceso a miembros hace referencia a una función no miembro.  
  
4.  El ejemplo siguiente genera el error C2597 y muestra cómo corregirlo:  
  
```  
// C2597.cpp  
// compile with: /c  
struct s1 {  
   static void func();  
   static void func2(s1&);  
   int i;  
};  
  
void s1::func() {  
   i = 1;    // C2597 - static function can't access non-static data member  
}  
  
// OK - fix by passing an instance of s1  
void s1::func2(s1& a) {  
   a.i = 1;  
}  
```