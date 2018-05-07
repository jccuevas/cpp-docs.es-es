---
title: Compilador advertencia (nivel 4) C4238 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4238
dev_langs:
- C++
helpviewer_keywords:
- C4238
ms.assetid: 5d4051d3-7b0f-43ea-8c8d-d194bfdceb71
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 06dbec01da8d1b47cb7b93c90a22ae5266e9b4c8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4238"></a>Advertencia del compilador (nivel 4) C4238
ha utilizado una extensión no estándar: rvalue de clase utilizado como valor l  
  
 Por compatibilidad con versiones anteriores de Visual C++, las extensiones de Microsoft (**/Ze**) le permiten utilizar un tipo de clase como un valor r en un contexto que implícita o explícitamente tome su dirección. En algunos casos, como en el ejemplo siguiente, esto puede ser peligroso.  
  
## <a name="example"></a>Ejemplo  
  
```  
// C4238.cpp  
// compile with: /W4 /c  
struct C {  
   C() {}  
};  
  
C * pC = &C();   // C4238  
```  
  
 Esta práctica genera un error en la compatibilidad con ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).