---
title: Compilador advertencia (nivel 1) C4917 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4917
dev_langs: C++
helpviewer_keywords: C4917
ms.assetid: c05e2610-4a5d-4f4b-a99b-c15fd7f1d5f1
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a3b5d930b0c8a79542526adcd174a9ed6a0a8db4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4917"></a>Advertencia del compilador (nivel 1) C4917
'declarador': un GUID solo puede asociarse con una clase, interfaz o espacio de nombres  
  
Una estructura definida por el usuario no sea [clase](../../cpp/class-cpp.md), [interfaz](../../cpp/interface.md), o [espacio de nombres](../../cpp/namespaces-cpp.md) no puede tener un GUID.  
  
De forma predeterminada, esta advertencia está desactivada. Vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md) para más información.  
  
## <a name="example"></a>Ejemplo  
El ejemplo de código siguiente genera C4917:  
  
```cpp  
// C4917.cpp  
// compile with: /W1  
#pragma warning(default : 4917)  
__declspec(uuid("00000000-0000-0000-0000-000000000001")) struct S  
{  
} s;   // C4917, don't put uuid on a struct  
  
int main()  
{  
}  
```