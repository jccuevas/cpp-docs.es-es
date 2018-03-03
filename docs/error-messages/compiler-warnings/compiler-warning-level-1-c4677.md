---
title: Compilador advertencia (nivel 1) C4677 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4677
dev_langs:
- C++
helpviewer_keywords:
- C4677
ms.assetid: a8d656a1-e2ff-4f8b-9028-201765131026
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7af724ad56c3a84ffb8ef48e13d14bee97db14df
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4677"></a>Advertencia del compilador (nivel 1) C4677
'función': la firma de un miembro no privado contiene un tipo privado de ensamblado 'tipo_privado'  
  
 Un tipo que tiene accesibilidad pública fuera del ensamblado utiliza un tipo que tiene acceso privado fuera del ensamblado. Un componente que hace referencia al tipo de ensamblado público no podrá usar el miembro de tipo o los miembros que hacen referencia al tipo privado de ensamblado.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C4677.  
  
```  
// C4677.cpp  
// compile with: /clr /c /W1  
delegate void TestDel();  
public delegate void TestDel2();  
  
public ref class MyClass {  
public:  
   static event TestDel^ MyClass_Event;   // C4677  
   static event TestDel2^ MyClass_Event2;   // OK  
};  
```