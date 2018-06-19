---
title: Error del compilador C2192 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2192
dev_langs:
- C++
helpviewer_keywords:
- C2192
ms.assetid: a147197e-e72d-4620-939b-f9e08d7c7c12
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a97b0885dd626c992ab55703038838aa743e30d0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33168703"
---
# <a name="compiler-error-c2192"></a>Error del compilador C2192
declaración de parámetro 'número' es diferente  
  
 Una función de C se ha declarado una segunda vez con una lista de parámetros distinta. C no admite funciones sobrecargadas.  
  
 El ejemplo siguiente genera C2192:  
  
```  
// C2192.c  
// compile with: /Za /c  
void func( float, int );  
void func( int, float );   // C2192, different parameter list  
void func2( int, float );   // OK  
```