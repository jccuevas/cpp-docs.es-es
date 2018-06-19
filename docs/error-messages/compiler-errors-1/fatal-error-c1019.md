---
title: Error irrecuperable C1019 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1019
dev_langs:
- C++
helpviewer_keywords:
- C1019
ms.assetid: c4f8968b-bc62-4200-b3ca-69d06c163236
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 119ff2df1554467762c0b960e80ad4c241517628
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33198682"
---
# <a name="fatal-error-c1019"></a>Error irrecuperable C1019
#else inesperada  
  
 La directiva `#else` aparece fuera de una construcción `#if`, `#ifdef`o `#ifndef` . Use `#else` solamente dentro de una de estas construcciones.  
  
 El ejemplo siguiente genera la advertencia C1019:  
  
```  
// C1019.cpp  
#else   // C1019  
#endif  
  
int main() {}  
```  
  
 Posible resolución:  
  
```  
// C1019b.cpp  
#if 1  
#else  
#endif  
  
int main() {}  
```