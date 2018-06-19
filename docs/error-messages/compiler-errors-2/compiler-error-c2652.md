---
title: C2652 de Error del compilador | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2652
dev_langs:
- C++
helpviewer_keywords:
- C2652
ms.assetid: 6e3d1a90-a989-4088-8afd-dc82f6a2d66f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 576aef31268c0cdce09162fc367358e0ed044429
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33232204"
---
# <a name="compiler-error-c2652"></a>C2652 de Error del compilador
'identificador': constructor de copias no válido: primer parámetro no debe ser un 'identificador'  
  
 El primer parámetro del constructor de copias tiene el mismo tipo que la clase, estructura o unión para el que está definido. El primer parámetro puede ser una referencia al tipo, pero no el propio tipo.  
  
 El ejemplo siguiente genera C2651:  
  
```  
// C2652.cpp  
// compile with: /c  
class A {  
   A( A );   // C2652 takes an A  
};  
class B {  
   B( B& );   // OK, reference to B  
};  
```