---
title: Error del compilador C3354 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3354
dev_langs:
- C++
helpviewer_keywords:
- C3354
ms.assetid: 185de401-231e-4999-a149-172ee4c69d84
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3b4bcc36580a453932068350f01b53c5f09f2d69
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3354"></a>Error del compilador C3354
'function': la función usada para crear un delegado no puede tener el tipo de valor devuelto 'type'  
  
 Los tipos siguientes no son válidos como tipos de valor devuelto para un `delegate`:  
  
-   De puntero a función  
  
-   Puntero a miembro  
  
-   Puntero a función miembro  
  
-   Referencia a función  
  
-   Referencia a función miembro  
  
 El ejemplo siguiente genera la advertencia C3354:  
  
```  
// C3354_2.cpp  
// compile with: /clr /c  
using namespace System;  
typedef void ( *VoidPfn )();  
  
delegate VoidPfn func(); // C3354  
// try the following line instead  
// delegate  void func();  
```  
