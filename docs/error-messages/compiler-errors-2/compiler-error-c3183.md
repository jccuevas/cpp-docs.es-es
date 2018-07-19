---
title: Error de compilador el error C3183 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3183
dev_langs:
- C++
helpviewer_keywords:
- C3183
ms.assetid: dbd0f020-c739-43c9-947e-9ce21537331b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4520922550dfcb5050c5e8a122910acf4b124934
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33252476"
---
# <a name="compiler-error-c3183"></a>Error C3183 de Error de compilador
no se puede definir class, struct o union sin nombre dentro del tipo administrado o WinRT 'type'  
  
Un tipo que se incrusta en un tipo administrado o WinRT debe tener un nombre.  
  
El ejemplo siguiente genera el error C3183:  
  
```  
// C3183a.cpp  
// compile with: /clr /c  
ref class Test  
{  
   ref class  
   {  // C3183, delete class or name it  
      int a;  
      int b;  
   };  
};  
```  
