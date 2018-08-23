---
title: Compilador advertencia (nivel 1) C4114 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4114
dev_langs:
- C++
helpviewer_keywords:
- C4114
ms.assetid: 3983e1c6-e8bb-46dc-8894-e1827db48797
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9969f58b24defdb3dfa8a96437769d0b19e4569e
ms.sourcegitcommit: b92ca0b74f0b00372709e81333885750ba91f90e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/16/2018
ms.locfileid: "42545901"
---
# <a name="compiler-warning-level-1-c4114"></a>Compilador advertencia (nivel 1) C4114
el mismo calificador de tipo se ha utilizado más de una vez  
  
 Una definición o declaración de tipo utiliza un calificador de tipo (**const**, **volátil**, **firmado**, o **sin signo**) más de una vez. Esto hace que una advertencia con las extensiones de Microsoft (/Ze) y un error en la compatibilidad con ANSI (/Za).  
  
 El ejemplo siguiente genera C4114:  
  
```  
// C4114.cpp  
// compile with: /W1 /c  
volatile volatile int i;   // C4114  
```  
  
 El ejemplo siguiente genera C4114:  
  
```  
// C4114_b.cpp  
// compile with: /W1 /c  
static const int const * ii;   // C4114  
static const int * const iii;   // OK  
```
