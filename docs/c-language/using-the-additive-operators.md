---
title: Usar los operadores de adición | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- operators [C++], addition
- additive operators
ms.assetid: 7d54841e-436d-4ae8-9865-1ac1829e6f22
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 44259ef77e5f09a1723064683c6900e425eb35c0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="using-the-additive-operators"></a>Usar los operadores de adición
En los ejemplos siguientes, que muestran los operadores de suma y resta, se usan estas declaraciones:  
  
```  
int i = 4, j;  
float x[10];  
float *px;  
```  
  
 Estas instrucciones son equivalentes:  
  
```  
px = &x[4 + i];  
px = &x[4] + i;    
```  
  
 El valor de `i` se multiplica por la longitud de un valor **float** y se agrega a `&x[4]`. El valor del puntero resultante es la dirección de `x[8]`.  
  
```  
j = &x[i] - &x[i-2];  
```  
  
 En este ejemplo, la dirección del tercer elemento de `x` (proporcionado por `x[i-2]`) se resta de la dirección del quinto elemento de `x` (proporcionado por `x[i]`). La diferencia se divide por la longitud de un valor **float**; el resultado es el valor entero 2.  
  
## <a name="see-also"></a>Vea también  
 [Operadores de adición de C](../c-language/c-additive-operators.md)