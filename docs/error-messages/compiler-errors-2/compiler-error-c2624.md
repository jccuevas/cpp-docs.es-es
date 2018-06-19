---
title: C2624 de Error del compilador | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2624
dev_langs:
- C++
helpviewer_keywords:
- C2624
ms.assetid: 32f2ec15-a7cd-4049-a64b-131746d3152b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d9edeb5bdef57663d29bb4cfe5427e5bc3f43b7d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33230669"
---
# <a name="compiler-error-c2624"></a>C2624 de Error del compilador
las clases locales no se puede usar para declarar variables 'extern'  
  
 Una clase o estructura local no se puede usar para declarar `extern` variables.  
  
 El ejemplo siguiente genera C2624:  
  
```  
// C2624.cpp  
int main() {  
   struct C {};  
   extern C ac;   // C2624  
}  
```