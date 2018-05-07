---
title: Error del compilador C2537 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2537
dev_langs:
- C++
helpviewer_keywords:
- C2537
ms.assetid: aee81d8e-300e-4a8b-b6c4-b3828398b34e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6100f77d3a1487bfa1eb12a78ac8187cec43fe64
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2537"></a>Error del compilador C2537
'especificador': especificación de vinculación no válida  
  
 Causas posibles:  
  
1.  No se admite el especificador de vinculación. Se admite solo el especificador de vinculación "C".  
  
2.  Vinculación de "C" se especifica más de una función de un conjunto de funciones sobrecargadas. Esto no está permitido.  
  
 El ejemplo siguiente genera C2537:  
  
```  
// C2537.cpp  
// compile with: /c  
extern "c" void func();   // C2537  
extern "C" void func2();   // OK  
```