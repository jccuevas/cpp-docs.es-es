---
title: "numérico (STL/CLR) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: <cliext/numeric>
dev_langs: C++
helpviewer_keywords:
- numeric functions [STL/CLR]
- <cliext/numeric> header [STL/CLR]
- <numeric> header [STL/CLR]
ms.assetid: 1dc4d9a3-e734-459c-9678-5d9be0ef4c79
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 99cac71e9de9e4022b6d3f005dff2ff6520b99e2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="numeric-stlclr"></a>numeric (STL/CLR)
Define las funciones de plantilla de contenedor que realizan los algoritmos proporcionados para el procesamiento numérico.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
#include <cliext/numeric>  
```  
  
## <a name="functions"></a>Funciones  
  
|Función|Descripción|  
|--------------|-----------------|  
|[accumulate (STL/CLR)](../dotnet/accumulate-stl-clr.md)|Calcula la suma de todos los elementos en un intervalo especificado incluidos algunos valores iniciales mediante el cálculo de sumas parciales sucesivas, o calcula el resultado de los resultados parciales sucesivos obtenidos de manera similar mediante el uso de una operación binaria determinada distinta de la suma.|  
|[adjacent_difference (STL/CLR)](../dotnet/adjacent-difference-stl-clr.md)|Calcula las diferencias sucesivas entre cada elemento y su predecesor en un intervalo de entrada, y pone los resultados en un intervalo de destino; o calcula el resultado de un procedimiento generalizado donde la operación de diferencia se reemplaza por otra operación binaria especificada.|  
|[inner_product (STL/CLR)](../dotnet/inner-product-stl-clr.md)|Calcula la suma del producto de elementos de dos intervalos y la agrega a un valor inicial especificado, o calcula el resultado de un procedimiento general donde las operaciones binarias de suma y de producto se reemplazan por otras operaciones binarias especificadas.|  
|[partial_sum (STL/CLR)](../dotnet/partial-sum-stl-clr.md)|Calcula una serie de sumas en un intervalo de entrada desde el primer elemento hasta el `i`elemento th y almacena el resultado de cada de esas sumas en `i`elemento de un intervalo de destino o calcula el resultado de un procedimiento generalizado donde la operación de suma se reemplaza por otra operación binaria especificada.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/numeric >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [Referencia de la biblioteca STL/CLR](../dotnet/stl-clr-library-reference.md)