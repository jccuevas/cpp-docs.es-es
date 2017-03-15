---
title: Compilador advertencia (nivel 1) C4677 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4677
dev_langs:
- C++
helpviewer_keywords:
- C4677
ms.assetid: a8d656a1-e2ff-4f8b-9028-201765131026
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 477b5def0b956dc06aa107003f93adea6ca1437c
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-1-c4677"></a>Advertencia del compilador (nivel 1) C4677
'función': la firma de un miembro no privado contiene un tipo privado de ensamblado de 'tipo_privado'  
  
 Un tipo que tenga accesibilidad pública fuera del ensamblado utiliza un tipo que tiene acceso privado fuera del ensamblado. Un componente que hace referencia al tipo de ensamblado público no podrá utilizar el miembro de tipo o los miembros que hacen referencia al tipo privado de ensamblado.  
  
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
