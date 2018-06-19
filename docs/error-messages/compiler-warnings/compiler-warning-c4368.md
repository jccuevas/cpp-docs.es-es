---
title: Advertencia del compilador C4368 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4368
dev_langs:
- C++
helpviewer_keywords:
- C4368
ms.assetid: cb85bcee-fd3d-4aa5-b626-2324f07a4f1b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a3a7e53c979a3b13bde205a4546c486061a17110
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33270501"
---
# <a name="compiler-warning-c4368"></a>Advertencia del compilador C4368
no puede definir 'miembro' como miembro de 'tipo' administrado: no se admiten tipos mixtos  
  
 No puede incrustar un miembro de datos nativo en un tipo CLR.  
  
 Es posible, sin embargo, declarar un puntero a un tipo nativo y controlar su duración en el constructor, destructor y finalizador de la clase administrada. Para obtener más información, consulte [destructores y finalizadores](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).  
  
 Esta advertencia siempre se emite como error. Use la [advertencia](../../preprocessor/warning.md) pragma para deshabilitar C4368.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera del C4368.  
  
```  
// C4368.cpp  
// compile with: /clr /c  
struct N {};  
ref struct O {};  
ref struct R {  
    R() : m_p( new N ) {}  
    ~R() { delete m_p; }  
  
   property N prop;   // C4368  
   int i[10];   // C4368  
  
   property O ^ prop2;   // OK  
   N * m_p;   // OK  
};  
```