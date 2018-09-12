---
title: Matrices multidimensionales (C) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- arrays [C], multidimensional
- multidimensional arrays
- subscript expressions
ms.assetid: 4ba5c360-1f17-4575-b370-45f62e1f2bc2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d2257ff9be5988ed6a08dd5d152c83910c6edc88
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43214724"
---
# <a name="multidimensional-arrays-c"></a>Matrices multidimensionales (C)
Una expresión de subíndice también puede tener varios subíndices, como se indica a continuación:  
  
```  
expression1 [ expression2 ] [ expression3 ] ...  
```  
  
 Las expresiones de subíndice se asocian de izquierda a derecha. La expresión de subíndice del extremo izquierdo, *expression1* **[** *expression2* **]**, se evalúa primero. La dirección resultante de agregar *expression1* y *expression2* forma una expresión de puntero; entonces, se agrega *expression3* a esta expresión de puntero para formar una nueva expresión de puntero, y así sucesivamente, hasta que se haya agregado la última expresión de subíndice. El operador de direccionamiento indirecto (<strong>\*</strong>) se aplica después de que se evalúe la última expresión de subíndice, a menos que el valor del puntero final apunte a un tipo de matriz (véanse los ejemplos a continuación).  
  
 Las expresiones con varios subíndices hacen referencia a elementos de “matrices multidimensionales”. Una matriz multidimensional es una matriz cuyos elementos son matrices. Por ejemplo, el primer elemento de una matriz tridimensional es una matriz con dos dimensiones.  
  
## <a name="examples"></a>Ejemplos  
 En los ejemplos siguientes, una matriz denominada `prop` se declara con tres elementos, cada uno de los cuales es una matriz de 4 por 6 de valores `int`.  
  
```  
int prop[3][4][6];  
int i, *ip, (*ipp)[6];  
```  
  
 Una referencia a la matriz `prop` tendrá el siguiente aspecto:  
  
```  
i = prop[0][0][1];  
```  
  
 En el ejemplo anterior se muestra cómo hacer referencia al segundo elemento individual `int` de `prop`. Las matrices se almacenan por fila, por lo que el último subíndice es el que cambia más rápidamente; la expresión `prop[0][0][2]` hace referencia al siguiente elemento (el tercero) de la matriz, y así sucesivamente.  
  
```  
i = prop[2][1][3];  
```  
  
 Esta instrucción es una referencia más compleja a un elemento individual de `prop`. La expresión se evalúa de la siguiente forma:  
  
1.  El primer subíndice, `2`, se multiplica por el tamaño de una matriz de 4 por 6 de valores `int` y se suma al valor del puntero `prop`. El resultado apunta a la tercera matriz de 4 por 6 de `prop`.  
  
2.  El segundo subíndice, `1`, se multiplica por el tamaño de la matriz de 6 elementos `int` y se suma a la dirección representada por `prop[2]`.  
  
3.  Cada elemento de la matriz de 6 elementos es un valor `int`, por lo que el subíndice final, `3`, se multiplica por el tamaño de un `int` antes de que se sume a `prop[2][1]`. El puntero resultante apunta al cuarto elemento de la matriz de 6 elementos.  
  
4.  El operador de direccionamiento indirecto se aplica al valor del puntero. El resultado es el elemento `int` en esa dirección.  
  
 Estos dos ejemplos muestran casos en los que no se aplica el operador de direccionamiento indirecto.  
  
```  
ip = prop[2][1];  
  
ipp = prop[2];  
```  
  
 En la primera de estas instrucciones, la expresión `prop[2][1]` es una referencia válida a la matriz tridimensional `prop`; hace referencia a una matriz de 6 elementos (declarada anteriormente). Como el valor del puntero apunta a una matriz, no se aplica el operador de direccionamiento indirecto.  
  
 De igual forma, el resultado de la expresión `prop[2]` en la segunda instrucción `ipp = prop[2];` es un valor de puntero que apunta a una matriz bidimensional.  
  
## <a name="see-also"></a>Vea también  
 [Operador de subíndice:](../cpp/subscript-operator.md)