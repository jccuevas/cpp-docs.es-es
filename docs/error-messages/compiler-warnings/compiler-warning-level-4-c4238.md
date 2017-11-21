---
title: Compilador advertencia (nivel 4) C4238 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4238
dev_langs: C++
helpviewer_keywords: C4238
ms.assetid: 5d4051d3-7b0f-43ea-8c8d-d194bfdceb71
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 32e8b4b252ed1da4bef785032929e615a6c73bc2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
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