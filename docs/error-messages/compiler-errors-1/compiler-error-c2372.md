---
title: Error del compilador C2372 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2372
dev_langs:
- C++
helpviewer_keywords:
- C2372
ms.assetid: 406bea63-c8d3-4231-9d26-c70af6980840
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 864162b02a2c7575809887bb638bb703219eea71
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33194871"
---
# <a name="compiler-error-c2372"></a>Error del compilador C2372
'identificador': nueva definición; diferentes tipos de direccionamiento indirecto  
  
 El identificador ya está definido con un tipo derivado distinto.  
  
 El ejemplo siguiente genera la advertencia C2326:  
  
```  
// C2372.cpp  
// compile with: /c  
extern int *fp;  
extern int fp[];   // C2372  
extern int fp2[];   // OK  
```