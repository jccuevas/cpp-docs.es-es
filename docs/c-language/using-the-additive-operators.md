---
title: "Usar los operadores de adición | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- operators [C++], addition
- additive operators
ms.assetid: 7d54841e-436d-4ae8-9865-1ac1829e6f22
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 94e2a63412e4fecd5f358659cc4bf02f90df57ad
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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