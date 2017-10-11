---
title: C3194 de Error del compilador | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3194
dev_langs:
- C++
helpviewer_keywords:
- C3194
ms.assetid: 49d3ffc6-eff6-4b46-865b-18811692a8bb
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 4ddfc0c87f4f58850eec595dcf35436590177283
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3194"></a>C3194 de Error del compilador
'member': un tipo de valor no puede tener un operador de asignación  
  
 Funciones miembro especiales que requieren una invocación automática por el compilador, por ejemplo, un constructor de copias o el operador de asignación de copia no se admiten dentro de una clase de valor.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C3194.  
  
```  
// C3194.cpp  
// compile with: /clr /c  
value struct MyStruct {  
   MyStruct& operator= (const MyStruct& i) { return *this; }   // C3194  
};  
  
ref struct MyStruct2 {  
   MyStruct2% operator= (const MyStruct2% i) { return *this; }   // OK  
};  
```
