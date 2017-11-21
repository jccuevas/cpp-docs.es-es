---
title: search_n (STL/CLR) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::search_n
dev_langs: C++
helpviewer_keywords: search_n function [STL/CLR]
ms.assetid: 34d9fd07-b160-4b1e-a632-303200740dfc
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: bdf58555a995b5be0c5726f3136afc8eafd64bfc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="searchn-stlclr"></a>search_n (STL/CLR)
Busca la primera subsecuencia de un intervalo en la que un número especificado de elementos tienen un valor determinado o una relación con ese valor según lo especificado por un predicado binario.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<class _FwdIt1, class _Diff2, class _Ty> inline  
    _FwdIt1 search_n(_FwdIt1 _First1, _FwdIt1 _Last1,  
        _Diff2 _Count, const _Ty& _Val);  
template<class _FwdIt1, class _Diff2, class _Ty, class _Pr> inline  
    _FwdIt1 search_n(_FwdIt1 _First1, _FwdIt1 _Last1,  
        _Diff2 _Count, const _Ty& _Val, _Pr _Pred);  
```  
  
## <a name="remarks"></a>Comentarios  
 Esta función comporta igual que la función de la biblioteca estándar de C++ `search_n`. Para obtener más información, consulte [search_n](../standard-library/algorithm-functions.md#search_n).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/algoritmo >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)