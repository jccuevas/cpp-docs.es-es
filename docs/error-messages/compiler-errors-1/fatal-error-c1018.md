---
title: Error irrecuperable C1018 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1018
dev_langs:
- C++
helpviewer_keywords:
- C1018
ms.assetid: 2ceb8a99-30b2-4b80-bf42-e9f3305b3c52
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 121ec73658527ff03e3cbc4871db78a5d00b50d1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33226436"
---
# <a name="fatal-error-c1018"></a>Error irrecuperable C1018
#elif inesperada  
  
 La directiva `#elif` aparece fuera de una construcción `#if`, `#ifdef`o `#ifndef` . Use `#elif` solamente dentro de una de estas construcciones.  
  
 El ejemplo siguiente genera la advertencia C1018:  
  
```  
// C1018.cpp  
#elif      // C1018  
#endif  
  
int main() {}  
```  
  
 Posible solución:  
  
```  
// C1018b.cpp  
#if 1  
#elif  
#endif  
  
int main() {}  
```