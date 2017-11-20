---
title: set_difference (STL/CLR) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::set_difference
dev_langs: C++
helpviewer_keywords: set_difference function [STL/CLR]
ms.assetid: 47a34d92-53d7-4065-9302-9e2e70e46c4d
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5aff7d5518e019ad7e261a464b0096420a4a0c7b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="setdifference-stlclr"></a>set_difference (STL/CLR)
Agrupa todos los elementos que pertenecen a un intervalo de origen ordenado, pero no a un segundo intervalo de origen ordenado, en un único intervalo de destino ordenado, donde el criterio de ordenación se puede especificar mediante un predicado binario.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<class _InIt1, class _InIt2, class _OutIt> inline  
    _OutIt set_difference(_InIt1 _First1, _InIt1 _Last1,  
        _InIt2 _First2, _InIt2 _Last2,_OutIt _Dest);  
template<class _InIt1, class _InIt2, class _OutIt, class _Pr> inline  
    _OutIt set_difference(_InIt1 _First1, _InIt1 _Last1,  
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest, _Pr _Pred);  
```  
  
## <a name="remarks"></a>Comentarios  
 Esta función comporta igual que la función de la biblioteca estándar de C++ `set_difference`. Para obtener más información, consulte [set_difference](../standard-library/algorithm-functions.md#set_difference).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/algoritmo >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)