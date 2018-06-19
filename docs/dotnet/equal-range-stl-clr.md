---
title: equal_range (STL/CLR) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::equal_range
dev_langs:
- C++
helpviewer_keywords:
- equal_range function [STL/CLR]
ms.assetid: 1b2e76c3-6b52-486d-9785-2639b54277fd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 9001d4b39b1b20e2caa7b5d81ac3b06d42042071
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33105873"
---
# <a name="equalrange-stlclr"></a>equal_range (STL/CLR)
Busca un par de posiciones en un intervalo ordenado; la primera es menor o equivalente a la posición de un elemento especificado y la segunda es mayor que la posición del elemento, donde el sentido de equivalencia o de ordenación empleado para establecer las posiciones en la secuencia se puede especificar con un predicado binario.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<class _FwdIt, class _Ty> inline  
    _PAIR_TYPE(_FwdIt) equal_range(_FwdIt _First, _FwdIt _Last,  
        const _Ty% _Val);  
template<class _FwdIt, class _Ty, class _Pr> inline  
    _PAIR_TYPE(_FwdIt) equal_range(_FwdIt _First, _FwdIt _Last,  
        const _Ty% _Val, _Pr _Pred);  
```  
  
## <a name="remarks"></a>Comentarios  
 Esta función comporta igual que la función de la biblioteca estándar de C++ `equal_range`. Para obtener más información, consulte [equal_range](../standard-library/algorithm-functions.md#equal_range).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/algoritmo >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)