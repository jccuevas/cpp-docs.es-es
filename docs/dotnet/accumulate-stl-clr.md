---
title: acumular (STL/CLR) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::accumulate
dev_langs:
- C++
helpviewer_keywords:
- accumulate function [STL/CLR]
ms.assetid: b80e1ef1-1858-4c1d-817b-c42ad1f17a2f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d9fefc3e7e7a2838891488996518b405972ba0f8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="accumulate-stlclr"></a>accumulate (STL/CLR)
Calcula la suma de todos los elementos en un intervalo especificado incluidos algunos valores iniciales mediante el cálculo de sumas parciales sucesivas, o calcula el resultado de los resultados parciales sucesivos obtenidos de manera similar mediante el uso de una operación binaria determinada distinta de la suma.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<class _InIt, class _Ty> inline  
    _Ty accumulate(_InIt _First, _InIt _Last, _Ty _Val);  
template<class _InIt, class _Ty, class _Fn2> inline  
    _Ty accumulate(_InIt _First, _InIt _Last, _Ty _Val, _Fn2 _Func);  
```  
  
## <a name="remarks"></a>Comentarios  
 Esta función comporta igual que la función numérica de la biblioteca estándar de C++ `accumulate`. Para obtener más información, consulte [acumular](../standard-library/numeric-functions.md#accumulate).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/numeric >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [numeric (STL/CLR)](../dotnet/numeric-stl-clr.md)