---
title: Error del compilador C3299 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3299
dev_langs:
- C++
helpviewer_keywords:
- C3299
ms.assetid: 7cabdf01-bceb-404f-9401-cdd9c7fc1641
caps.latest.revision: 4
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 3612762f397914b6058516db7d8f56b840873c1e
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3299"></a>Error del compilador C3299
'member_function': no puede especificar restricciones; estas se heredan del método base  
  
 Al reemplazar una función miembro genérica, no puede especificar cláusulas de restricción (la repetición de las restricciones implica que las restricciones no se heredan).  
  
 Se heredarán las cláusulas de restricción en la función genérica que está reemplazando.  
  
 Para obtener más información, consulte [restricciones en parámetros de tipo genérico (C++ / CLI)](../../windows/constraints-on-generic-type-parameters-cpp-cli.md).  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera la advertencia C3299.  
  
```  
// C3299.cpp  
// compile with: /clr /c  
public ref struct R {  
   generic<class T>   
   where T : R  
   virtual void f();  
};  
  
public ref struct S : R {  
   generic<class T>   
   where T : R   // C3299  
   virtual void f() override;  
};  
```
