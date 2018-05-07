---
title: Error del compilador C2299 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2299
dev_langs:
- C++
helpviewer_keywords:
- C2299
ms.assetid: d001c2bc-f6fd-47aa-8e42-0eb824d6441d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e21213f08e25050932274a64d0ed56db96f2a453
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
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