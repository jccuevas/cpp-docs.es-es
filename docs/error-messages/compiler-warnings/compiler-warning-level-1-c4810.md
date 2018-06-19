---
title: Compilador advertencia (nivel 1) C4810 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4810
dev_langs:
- C++
helpviewer_keywords:
- C4810
ms.assetid: 39e2cae0-9c1c-4ac1-aaa0-5f661d06085b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7a803a219520519f91605971d6fd515746cabb37
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33283343"
---
# <a name="compiler-warning-level-1-c4810"></a>Advertencia del compilador (nivel 1) C4810
valor de pragma pack(show) == n  
  
 Esta advertencia se emite cuando se usa la opción **show** de pragma [pack](../../preprocessor/pack.md) . *n* es el valor actual de pack.  
  
 Por ejemplo, el código siguiente muestra cómo funciona la advertencia C4810 con pragma pack:  
  
```  
// C4810.cpp  
// compile with: /W1 /LD  
// C4810 expected  
#pragma pack(show)  
#pragma pack(4)  
#pragma pack(show)  
```