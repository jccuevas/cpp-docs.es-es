---
title: adjacent_find (STL/CLR) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::adjacent_find
dev_langs:
- C++
helpviewer_keywords:
- adjacent_find function
ms.assetid: 48bf57ea-b128-4d16-97c5-01d8a378369f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: ce62fd96954adb122176e02eb19c00b63d4ebbb3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="adjacentfind-stlclr"></a>adjacent_find (STL/CLR)
Busca dos elementos adyacentes que son iguales o cumplen una condición especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<class _FwdIt> inline  
    _FwdIt adjacent_find(_FwdIt _First, _FwdIt _Last);  
template<class _FwdIt, class _Pr> inline  
    _FwdIt adjacent_find(_FwdIt _First, _FwdIt _Last, _Pr _Pred);  
```  
  
## <a name="remarks"></a>Comentarios  
 Esta función comporta igual que la función de la biblioteca estándar de C++ `adjacent_find`. Para obtener más información, consulte [adjacent_find](../standard-library/algorithm-functions.md#adjacent_find).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/algoritmo >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)