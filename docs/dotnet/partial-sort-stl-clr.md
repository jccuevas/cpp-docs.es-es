---
title: partial_sort (STL/CLR) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::partial_sort
dev_langs: C++
helpviewer_keywords: partial_sort function [STL/CLR]
ms.assetid: 5a73b275-aef0-4bda-8ae3-7c1196fe49c4
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 80de2072e6fdc7975d924c1a9c96b5033dfa978c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="partialsort-stlclr"></a>partial_sort (STL/CLR)
Organiza un número especificado de los elementos menores de un intervalo en un orden no descendente, o de acuerdo con un criterio de ordenación especificado por un predicado binario.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<class _RanIt> inline  
    void partial_sort(_RanIt _First, _RanIt _Mid, _RanIt _Last);  
template<class _RanIt, class _Pr> inline  
    void partial_sort(_RanIt _First, _RanIt _Mid, _RanIt _Last,  
        _Pr _Pred);  
```  
  
## <a name="remarks"></a>Comentarios  
 Esta función comporta igual que la función de la biblioteca estándar de C++ `partial_sort`. Para obtener más información, consulte [partial_sort](../standard-library/algorithm-functions.md#partial_sort).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/algoritmo >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)