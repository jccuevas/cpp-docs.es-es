---
title: swap_ranges (STL/CLR) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::swap_ranges
dev_langs: C++
helpviewer_keywords: swap_ranges function [STL/CLR]
ms.assetid: 3fb39a84-b088-48f1-8bb7-2bbe68b048a9
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1848fc7bc857e01e10d511f31403f89fb6bbf131
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="swapranges-stlclr"></a>swap_ranges (STL/CLR)
Intercambia los elementos de un intervalo con los elementos de otro intervalo del mismo tamaño.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<class _FwdIt1, class _FwdIt2> inline  
    _FwdIt2 swap_ranges(_FwdIt1 _First1, _FwdIt1 _Last1,  
        _FwdIt2 _First2);  
```  
  
## <a name="remarks"></a>Comentarios  
 Esta función comporta igual que la función de la biblioteca estándar de C++ `swap_ranges`. Para obtener más información, consulte [swap_ranges](../standard-library/algorithm-functions.md#swap_ranges).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/algoritmo >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)