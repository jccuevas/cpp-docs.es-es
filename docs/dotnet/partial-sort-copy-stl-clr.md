---
title: partial_sort_copy (STL/CLR) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::partial_sort_copy
dev_langs:
- C++
helpviewer_keywords:
- partial_sort_copy function [STL/CLR]
ms.assetid: ed4af83e-7554-4f6d-bf54-c56fa6210fe8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 99b60d3b3384cacd7c501ea1d8beb4e76131616b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33159839"
---
# <a name="partialsortcopy-stlclr"></a>partial_sort_copy (STL/CLR)
Copia los elementos de un intervalo de origen a un intervalo de destino donde los elementos de origen están ordenados por menor que u otro predicado binario especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<class _InIt, class _RanIt> inline  
    _RanIt partial_sort_copy(_InIt _First1, _InIt _Last1,  
        _RanIt _First2, _RanIt _Last2);  
template<class _InIt, class _RanIt, class _Pr> inline  
    _RanIt partial_sort_copy(_InIt _First1, _InIt _Last1,  
        _RanIt _First2, _RanIt _Last2, _Pr _Pred);  
```  
  
## <a name="remarks"></a>Comentarios  
 Esta función comporta igual que la función de la biblioteca estándar de C++ `partial_sort_copy`. Para obtener más información, consulte [partial_sort_copy](../standard-library/algorithm-functions.md#partial_sort_copy).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/algoritmo >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)