---
title: C2711 de Error del compilador | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2711
dev_langs:
- C++
helpviewer_keywords:
- C2711
ms.assetid: 9df9f808-7419-4e63-abdd-e6538ff0871f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fb2e5c904d7f6d865b94ea4fb4ba65be4c974f8b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33234280"
---
# <a name="compiler-error-c2711"></a>C2711 de Error del compilador
'función': esta función no se puede compilar como administrada, considere la posibilidad de usar #pragma no administrado  
  
 Algunas instrucciones impedirá que el compilador genere MSIL para la función de inclusión.  
  
 El ejemplo siguiente genera C2711:  
  
```  
// C2711.cpp  
// compile with: /clr  
// processor: x86  
using namespace System;  
value struct V {  
   static const t = 10;  
};  
  
void bar() {  
   V::t;  
   __asm int 3   // C2711 inline asm can't be compiled managed  
}  
```