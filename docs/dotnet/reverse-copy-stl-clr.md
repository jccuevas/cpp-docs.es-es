---
title: reverse_copy (STL/CLR) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::reverse_copy
dev_langs: C++
helpviewer_keywords: reverse_copy function [STL/CLR]
ms.assetid: 694e577a-0fa8-44f7-adde-6dd9f45adefd
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 69dbf8a9ff6c240d02e5f38ed4ed4d5f6bfcf072
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="reversecopy-stlclr"></a>reverse_copy (STL/CLR)
Invierte el orden de los elementos dentro de un intervalo de origen mientras los copia a un intervalo de destino.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<class _BidIt, class _OutIt> inline  
    _OutIt reverse_copy(_BidIt _First, _BidIt _Last, _OutIt _Dest);  
```  
  
## <a name="remarks"></a>Comentarios  
 Esta función comporta igual que la función de la biblioteca estándar de C++ `reverse_copy`. Para obtener más información, consulte [reverse_copy](../standard-library/algorithm-functions.md#reverse_copy).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/algoritmo >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)