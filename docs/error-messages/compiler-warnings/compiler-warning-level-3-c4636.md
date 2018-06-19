---
title: Compilador advertencia (nivel 3) C4636 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4636
dev_langs:
- C++
helpviewer_keywords:
- C4636
ms.assetid: 59112a0f-850f-41c6-bd84-8ae8dc84706a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c48c7d93846d4c313fa3a09c22e009f31bdd2224
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33290496"
---
# <a name="compiler-warning-level-3-c4636"></a>Advertencia del compilador (nivel 3) C4636
Comentario del documento XML aplicado a 'construcción': la etiqueta requiere que un atributo '' no esté vacío.  
  
 Una etiqueta, como `cref`, no tiene un valor.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera la advertencia C4636.  
  
```  
// C4636.cpp  
// compile with: /clr /doc /W3 /c  
/// <see cref=''/>  
// /// <see cref='System::Exception'/>  
ref struct A {   // C4636  
   void f(int);  
};  
  
// OK  
/// <see cref='System::Exception'/>  
ref struct B {  
   void f(int);  
};  
```