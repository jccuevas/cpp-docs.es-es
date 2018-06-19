---
title: Merge (STL/CLR) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::merge
dev_langs:
- C++
helpviewer_keywords:
- merge function [STL/CLR]
ms.assetid: e42d3396-63a4-438a-964d-83e90405102e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 09f9cc8d81eb4862607d2382f7d3d2ac033cf111
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33131184"
---
# <a name="merge-stlclr"></a>merge (STL/CLR)
Combina todos los elementos de dos intervalos de origen ordenados en un único intervalo de destino ordenado, donde el criterio de ordenación se puede especificar mediante un predicado binario.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<class _InIt1, class _InIt2, class _OutIt> inline  
    _OutIt merge(_InIt1 _First1, _InIt1 _Last1,  
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest);  
template<class _InIt1, class _InIt2, class _OutIt, class _Pr> inline  
    _OutIt merge(_InIt1 _First1, _InIt1 _Last1,  
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest, _Pr _Pred);  
```  
  
## <a name="remarks"></a>Comentarios  
 Esta función comporta igual que la función de la biblioteca estándar de C++ `merge`. Para obtener más información, consulte [mezcla](../standard-library/algorithm-functions.md#merge).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/algoritmo >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)