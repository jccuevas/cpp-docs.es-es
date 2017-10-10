---
title: C2178 de Error del compilador | Documentos de Microsoft
ms.custom: 
ms.date: 05/08/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2178
dev_langs:
- C++
helpviewer_keywords:
- C2178
ms.assetid: 79a14158-17f3-4221-bd06-9d675c49cef4
caps.latest.revision: 0
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: facb255b0c53a3de0e1d5c9f90de5835b25e3c32
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

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

