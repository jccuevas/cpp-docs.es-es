---
title: Compilador advertencia (nivel 4) C4295 | Documentos de Microsoft
ms.custom: ''
ms.date: 1/09/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4295
dev_langs:
- C++
helpviewer_keywords:
- C4295
ms.assetid: 20dbff85-9f62-4ca3-8fe9-079d4512006d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 815a669bc359121b13b1d636009cad81dc332304
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4295"></a>Advertencia del compilador (nivel 4) C4295
  
> '*matriz*': matriz es demasiado pequeña para incluir un carácter nulo de terminación  
  
Se inicializó una matriz, pero el último carácter de la matriz no es null; obtener acceso a la matriz como una cadena puede producir resultados inesperados.  
  
## <a name="example"></a>Ejemplo  
  
El ejemplo siguiente genera C4295. Para corregir este problema, podría declarar el tamaño de la matriz más grande para contener un carácter nulo final de la cadena de inicializador o podría utilizar una lista de inicializadores de matriz para hacer la intención clear que se trata de una matriz de `char`, no una cadena terminada en null.  
  
```C  
// C4295.c
// compile with: /W4


int main() {
   char a[3] = "abc";           // C4295
   char b[3] = {'d', 'e', 'f'}; // No warning
   a[0] = b[2];
}
```
