---
title: Error del compilador C2234 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2234
dev_langs: C++
helpviewer_keywords: C2234
ms.assetid: cfa42458-c803-4717-a017-9eca1c0cbfb0
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b556efc1e73ae04f749441e1888d46cd5499e8ea
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
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