---
title: count_if (STL/CLR) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::count_if
dev_langs:
- C++
helpviewer_keywords:
- count_if function [STL/CLR]
ms.assetid: a8aa149d-20b8-4b3f-917b-1ec66f178a5d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: e17e68471f42234d5f09c8c4792324765c5c0981
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="countif-stlclr"></a>count_if (STL/CLR)
Devuelve el número de elementos de un intervalo cuyos valores coinciden con una condición especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<class _InIt, class _Pr> inline  
    typename iterator_traits<_InIt>::difference_type  
        count_if(_InIt _First, _InIt _Last, _Pr _Pred);  
```  
  
## <a name="remarks"></a>Comentarios  
 Esta función comporta igual que la función de la biblioteca estándar de C++ `count_if`. Para obtener más información, consulte [count_if](../standard-library/algorithm-functions.md#count_if).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/algoritmo >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)