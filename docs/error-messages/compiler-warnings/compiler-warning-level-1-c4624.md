---
title: Compilador advertencia (nivel 1) C4624 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4624
dev_langs:
- C++
helpviewer_keywords:
- C4624
ms.assetid: 14f61769-d92e-482b-9515-debd87b30a66
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8d11bc5c8b5034fa305a22ba893c62faff18cc38
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4624"></a>Advertencia del compilador (nivel 1) C4624
'derived class': el destructor se definió implícitamente como eliminado porque un destructor de clase base es inaccesible o se ha eliminado  
  
 Un destructor no está accesible o se eliminó en una clase base y, por tanto, no se generó para una clase derivada. Cualquier intento de crear un objeto de este tipo en la pila provocará un error del compilador.  
  
 El ejemplo siguiente genera el error C4624 y muestra cómo corregirlo:  
  
```  
// C4624.cpp  
// compile with: /W1 /c  
class B {  
// Uncomment the following line to fix.  
// public:  
   ~B();  
};  
  
class D : public B {};   // C4624 B's destructor not public  
```