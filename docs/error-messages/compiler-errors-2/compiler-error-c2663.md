---
title: C2663 de Error del compilador | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2663
dev_langs:
- C++
helpviewer_keywords:
- C2663
ms.assetid: 1e93e368-fd52-42bf-9908-9b6df467c8c9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f39f516b32aaf1159d47726d01623e253ee8b383
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2663"></a>C2663 de Error del compilador
'función': número sobrecargas no tienen conversiones válidas para el puntero 'this'  
  
 El compilador no se pudo convertir `this` a cualquiera de las versiones sobrecargadas de la función miembro.  
  
 Este error puede deberse a invocar no`const` función miembro en un `const` objeto.  Soluciones posibles:  
  
1.  Quitar el `const` de la declaración del objeto.  
  
2.  Agregar `const` a una de las sobrecargas de función miembro.  
  
 El ejemplo siguiente genera C2663:  
  
```  
// C2663.cpp  
struct C {  
   void f() volatile {}  
   void f() {}  
};  
  
struct D {  
   void f() volatile;  
   void f() const {}  
};  
  
const C *pcc;  
const D *pcd;  
  
int main() {  
   pcc->f();    // C2663  
   pcd->f();    // OK  
}  
```