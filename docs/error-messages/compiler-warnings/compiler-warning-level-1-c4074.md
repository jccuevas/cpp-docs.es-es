---
title: Compilador advertencia (nivel 1) C4074 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4074
dev_langs:
- C++
helpviewer_keywords:
- C4074
ms.assetid: cd510e66-c338-4a86-a4d7-bfa1df9b16c3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9072728660ca78097a1e36e492670a614bb2b2f8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4074"></a>Compilador advertencia (nivel 1) C4074
inicializadores situados en el área de inicialización reservada para el compilador  
  
 El área de inicialización del compilador, que se especifica mediante [#pragma init_seg](../../preprocessor/init-seg.md), está reservada por Microsoft. Antes de la inicialización de la biblioteca de tiempo de ejecución de C puede ejecutar código en esta área.  
  
 El ejemplo siguiente genera C4074:  
  
```  
// C4074.cpp  
// compile with: /W1  
#pragma init_seg( compiler )   // C4074  
  
// try this line to resolve the warning  
// #pragma init_seg(user)  
  
int main() {  
}  
```