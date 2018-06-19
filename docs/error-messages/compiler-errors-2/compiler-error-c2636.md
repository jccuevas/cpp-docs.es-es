---
title: C2636 de Error del compilador | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2636
dev_langs:
- C++
helpviewer_keywords:
- C2636
ms.assetid: 379873ec-8d05-49f8-adf1-b067bc07bdb8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 61422fcf03cabd6d7c2ed8bca23b9170df7e52bc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33227577"
---
# <a name="compiler-error-c2636"></a>C2636 de Error del compilador
'identificador': puntero a miembro de referencia no es válido  
  
 Se ha declarado un puntero a un miembro de referencia.  
  
 El ejemplo siguiente genera C2636:  
  
```  
// C2636.cpp  
struct S {};  
int main() {  
   int &S::*prs;   // C2636  
   int S::*prs1;   // OK  
   int *S::*prs2;   // OK  
}  
```