---
title: C2698 de Error del compilador | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2698
dev_langs:
- C++
helpviewer_keywords:
- C2698
ms.assetid: 3ebfe395-c20b-4c56-9980-ca9ed8653382
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7c466e39702f1e408ad96d79c16c4a5953fa373f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33233822"
---
# <a name="compiler-error-c2698"></a>C2698 de Error del compilador
la declaración using para ' declaración 1' no puede coexistir con la declaración using existente para ' declaración 2'  
  
 Una vez que tenga un [mediante declaración](../../cpp/using-declaration.md) para un miembro de datos, cualquier uso no se permite la declaración en el mismo ámbito que utiliza el mismo nombre, tal y como funciones solo se pueden sobrecargar.  
  
 El ejemplo siguiente genera C2698:  
  
```  
// C2698.cpp  
struct A {  
   int x;  
};  
  
struct B {  
   int x;  
};  
  
struct C : A, B {  
   using A::x;  
   using B::x;   // C2698  
}  
```