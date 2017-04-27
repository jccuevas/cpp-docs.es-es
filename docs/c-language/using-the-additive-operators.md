---
title: "Usar los operadores de adición | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- operators [C++], addition
- additive operators
ms.assetid: 7d54841e-436d-4ae8-9865-1ac1829e6f22
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 04e23f9694193a05d48b7fcdff717d06e448e877
ms.lasthandoff: 04/01/2017

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
