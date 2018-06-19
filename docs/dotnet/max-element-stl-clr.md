---
title: max_element (STL/CLR) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::max_element
dev_langs:
- C++
helpviewer_keywords:
- max_element function [STL/CLR]
ms.assetid: c6274bae-1216-4285-b395-254280253dae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 84fb1fb7a3b99889f5a2926fcdb786316dd5abe5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33132692"
---
# <a name="maxelement-stlclr"></a>max_element (STL/CLR)
Busca la primera aparición del elemento mayor en un intervalo especificado donde el criterio de ordenación se puede especificar mediante un predicado binario.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<class _FwdIt> inline  
    _FwdIt max_element(_FwdIt _First, _FwdIt _Last);  
template<class _FwdIt, class _Pr> inline  
    _FwdIt max_element(_FwdIt _First, _FwdIt _Last, _Pr _Pred);  
```  
  
## <a name="remarks"></a>Comentarios  
 Esta función comporta igual que la función de la biblioteca estándar de C++ `max_element`. Para obtener más información, consulte [max_element](../standard-library/algorithm-functions.md#max_element).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/algoritmo >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)