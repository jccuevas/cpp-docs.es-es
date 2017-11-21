---
title: min_element (STL/CLR) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::min_element
dev_langs: C++
helpviewer_keywords: min_element function [STL/CLR]
ms.assetid: 2a9c6828-9722-454f-9c10-d4a184d4d21b
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7996e368abff6d82c346ff58eb19d2d53ff208d1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="minelement-stlclr"></a>min_element (STL/CLR)
Busca la primera aparición del menor elemento en un intervalo especificado donde el criterio de ordenación se puede especificar mediante un predicado binario.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<class _FwdIt> inline  
    _FwdIt min_element(_FwdIt _First, _FwdIt _Last);  
template<class _FwdIt, class _Pr> inline  
    _FwdIt min_element(_FwdIt _First, _FwdIt _Last, _Pr _Pred);  
```  
  
## <a name="remarks"></a>Comentarios  
 Esta función comporta igual que la función de la biblioteca estándar de C++ `min_element`. Para obtener más información, consulte [min_element](../standard-library/algorithm-functions.md#min_element).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/algoritmo >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)