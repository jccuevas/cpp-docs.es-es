---
title: Compilador advertencia (nivel 4) C4295 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4295
dev_langs: C++
helpviewer_keywords: C4295
ms.assetid: 20dbff85-9f62-4ca3-8fe9-079d4512006d
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5815aab6163c7dc6ffa8bf89bbf56259724d02b5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4295"></a>Advertencia del compilador (nivel 4) C4295
  
> '*matriz*': matriz es demasiado pequeña para incluir un carácter nulo de terminación  
  
 Se inicializó una matriz, pero el último carácter de la matriz no es null; obtener acceso a la matriz puede producir resultados inesperados.  
  
## <a name="example"></a>Ejemplo  
  
 El ejemplo siguiente genera C4295. Para corregir este problema, podría declarar el tamaño de la matriz más grande para contener una terminación null desde el inicializador.  
  
```C  
// C4295.c  
// compile with: /W4  
  
int main() {  
   char a[3] = "abc";   // C4295  
}  
```