---
title: remove_copy_if (STL/CLR) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::remove_copy_if
dev_langs:
- C++
helpviewer_keywords:
- remove_copy_if function [STL/CLR]
ms.assetid: 5307f5fe-b6bb-4968-8da1-fea84ab96655
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 1059916855822dcdc0fd2e17e15cf95cfab4d257
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="removecopyif-stlclr"></a>remove_copy_if (STL/CLR)
Copia elementos de un intervalo de origen a un intervalo de destino, excepto que los elementos que satisfacen un predicado no se copian, sin alterar el orden de los elementos restantes y devolver el final de un nuevo intervalo de destino.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<class _InIt, class _OutIt, class _Pr> inline  
    _OutIt remove_copy_if(_InIt _First, _InIt _Last, _OutIt _Dest,  
        _Pr _Pred);  
```  
  
## <a name="remarks"></a>Comentarios  
 Esta función comporta igual que la función de la biblioteca estándar de C++ `remove_copy_if`. Para obtener más información, consulte [remove_copy_if](../standard-library/algorithm-functions.md#remove_copy_if).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/algoritmo >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)