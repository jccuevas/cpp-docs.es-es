---
title: Compilador advertencia (nivel 1) C4688 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4688
dev_langs:
- C++
helpviewer_keywords:
- C4688
ms.assetid: a027df3c-b2b8-4c49-8539-c2bc42db74e8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 503f7783748407415ecd3a4ddbaafeb601b7c2b1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4688"></a>Advertencia del compilador (nivel 1) C4688
'constraint': la lista de restricciones contiene un tipo privado de ensamblado 'type'  
  
 Una lista de restricciones tiene un tipo privado de ensamblado, lo que significa que no estará disponible cuando se acceda al tipo desde fuera del ensamblado. Para más información, vea [Genéricos](../../windows/generics-cpp-component-extensions.md).  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera la advertencia C4688.  
  
```  
// C4688.cpp  
// compile with: /clr /c /W1  
ref struct A {};   // private type  
public ref struct B {};  
  
// Delete the following 3 lines to resolve.  
generic <class T>   
where T : A   // C4688  
public ref struct M {};  
  
generic <class T>   
where T : B  
public ref struct N {};  
```