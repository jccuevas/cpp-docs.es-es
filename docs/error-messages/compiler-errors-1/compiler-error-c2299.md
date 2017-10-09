---
title: Error del compilador C2299 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2299
dev_langs:
- C++
helpviewer_keywords:
- C2299
ms.assetid: d001c2bc-f6fd-47aa-8e42-0eb824d6441d
caps.latest.revision: 16
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 4c0b18818ac45dea56d94b6046c8772710f02f56
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2299"></a>Error del compilador C2299
'función': cambio de comportamiento: una especialización explícita no puede ser un constructor de copias o el operador de asignación de copia  
  
 Este error también puede generarse como resultado del trabajo de conformidad del compilador efectuado para Visual C++ 2005: las versiones anteriores de Visual C++ permitían la especialización explícita de un constructor de copias o un operador de asignación de copia.  
  
 Para solucionar el error C2299, hacer que el constructor de copias o el operador de asignación de una función de plantilla, pero en su lugar una función no es de plantilla que toma un tipo de clase. El código que llama al constructor de copias o el operador de asignación especificando explícitamente los argumentos de plantilla debe quitar los argumentos de plantilla.  
  
 El ejemplo siguiente genera el error C2299:  
  
```  
// C2299.cpp  
// compile with: /c  
class C {  
   template <class T>  
   C (T t);  
  
   template <> C (const C&);   // C2299  
   C (const C&);   // OK  
};  
```
