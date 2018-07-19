---
title: Compilador advertencia (nivel 1) C4618 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4618
dev_langs:
- C++
helpviewer_keywords:
- C4618
ms.assetid: 6ff10d0a-6d5b-4373-8196-1d57bb6b1611
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e53f8542983a6e15f353ff181efa280815fea9d8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33282527"
---
# <a name="compiler-warning-level-1-c4618"></a>Advertencia del compilador (nivel 1) C4618
parámetros de tipo pragma incluían una cadena vacía; se ha omitido pragma  
  
 Se proporcionó una cadena nula como argumento para una **#pragma**.  
  
 Se procesó la directiva pragma sin el argumento.  
  
 El ejemplo siguiente genera C4618:  
  
```  
// C4618.cpp  
// compile with: /W1 /LD  
#pragma code_seg("")   // C4618  
```