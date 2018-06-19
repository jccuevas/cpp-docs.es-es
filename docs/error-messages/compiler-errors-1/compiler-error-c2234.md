---
title: Error del compilador C2234 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2234
dev_langs:
- C++
helpviewer_keywords:
- C2234
ms.assetid: cfa42458-c803-4717-a017-9eca1c0cbfb0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0bba14bd704ba4d068fc5534f78a32f80b42046a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33169067"
---
# <a name="compiler-error-c2234"></a>Error del compilador C2234
'name': las matrices de referencias son válidas  
  
 Dado que no se permiten punteros a las referencias, las matrices de referencias no son posibles.  
  
 El ejemplo siguiente genera C2234:  
  
```  
// C2234.cpp  
int main() {  
   int i = 0, j = 0, k = 0, l = 0;  
   int &array[4] = {i,j,k,l};   // C2234  
   int array2[4] = {i,j,k,l};   // OK  
}  
```