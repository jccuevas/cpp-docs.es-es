---
title: adjacent_difference (STL/CLR) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::adjacent_difference
dev_langs: C++
helpviewer_keywords: adjacent_difference function
ms.assetid: 2b462e2e-b8f2-4b2e-9b87-5f688d8da9f4
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0be63f7032de5f6d3def4ba74f24a346785b7391
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="adjacentdifference-stlclr"></a>adjacent_difference (STL/CLR)
Calcula las diferencias sucesivas entre cada elemento y su predecesor en un intervalo de entrada, y pone los resultados en un intervalo de destino; o calcula el resultado de un procedimiento generalizado donde la operación de diferencia se reemplaza por otra operación binaria especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<class _InIt, class _OutIt> inline  
    _OutIt adjacent_difference(_InIt _First, _InIt _Last,  
        _OutIt _Dest);  
template<class _InIt, class _OutIt, class _Fn2> inline  
    _OutIt adjacent_difference(_InIt _First, _InIt _Last,  
        _OutIt _Dest, _Fn2 _Func);  
```  
  
## <a name="remarks"></a>Comentarios  
 Esta función comporta igual que la función numérica de la biblioteca estándar de C++ `adjacent_difference`. Para obtener más información, consulte [adjacent_difference](../standard-library/numeric-functions.md#adjacent_difference).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/numeric >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [numeric (STL/CLR)](../dotnet/numeric-stl-clr.md)