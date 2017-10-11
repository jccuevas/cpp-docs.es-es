---
title: Error del compilador C3612 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3612
dev_langs:
- C++
helpviewer_keywords:
- C3612
ms.assetid: aa6e3a2b-4afa-481c-98c1-1b6d1f82f869
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: dd430c7dbdfae88d80e073fa9e624f123c41f366
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3612"></a>Error del compilador C3612
'type': una clase sellada no puede ser abstracta  
  
Tipos definidos mediante `value` son sealed de forma predeterminada, y una clase es abstracta, a menos que implementa todos los métodos de su base. Una clase abstracta sealed no puede ser una clase base ni se puede crear instancias.  
  
Para obtener más información, consulte [clases y Structs](../../windows/classes-and-structs-cpp-component-extensions.md).  
  
## <a name="example"></a>Ejemplo  
El ejemplo siguiente genera C3612:  
  
```  
// C3612.cpp  
// compile with: /clr /c  
value struct V: public System::ICloneable {};   // C3612  
  
// OK  
value struct V2: public System::ICloneable {  
   Object^ Clone();  
};  
```
