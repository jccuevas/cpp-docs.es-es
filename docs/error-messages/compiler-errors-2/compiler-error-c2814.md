---
title: Error del compilador C2814 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2814
dev_langs:
- C++
helpviewer_keywords:
- C2814
ms.assetid: 7d165136-a08b-4497-a76d-60a21bb19404
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 75215a0df53606c8807cc275e86616c1ae8c6b42
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2814"></a>Error del compilador C2814
'miembro': un tipo nativo no se puede anidar dentro de un 'tipo' administrado o WinRT  
  
## <a name="example"></a>Ejemplo  
 Un tipo nativo no se puede anidar en un tipo CLR o WinRT. El ejemplo siguiente genera el error C2814 y muestra cómo corregirlo.  
  
```  
// C2814.cpp  
// compile with: /clr /c  
ref class A {  
   class B {};   // C2814  
   ref class C {};   // OK  
};  
```  
