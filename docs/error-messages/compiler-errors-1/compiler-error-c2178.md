---
title: C2178 de Error del compilador | Documentos de Microsoft
ms.custom: ''
ms.date: 05/08/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2178
dev_langs:
- C++
helpviewer_keywords:
- C2178
ms.assetid: 79a14158-17f3-4221-bd06-9d675c49cef4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3727a66554b2e128061820df160c02a1370ebb74
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33171301"
---
# <a name="compiler-error-c2178"></a>C2178 de Error del compilador  
  
'*identificador*'no se pueden declarar con'*especificador*' especificador  
  
Un `mutable` especificador se usó en una declaración, pero no se permite el especificador en este contexto.  
  
El `mutable` especificador pueden aplicarse únicamente a los nombres de miembros de datos de clase y no se puede aplicar a los nombres declarados `const` o `static`y no se puede aplicar para hacer referencia a miembros.  
  
## <a name="example"></a>Ejemplo  
  
El ejemplo siguiente muestra cómo puede producirse C2178 y cómo corregirlo.  
  
```  
// C2178.cpp
// compile with: cl /c /W4 C2178.cpp

class S {
    mutable const int i; // C2178
    // To fix, declare either const or mutable, not both.
};

mutable int x = 4; // C2178
// To fix, remove mutable keyword
```  
