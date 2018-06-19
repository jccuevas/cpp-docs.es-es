---
title: Reemplazar (STL/CLR) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::replace
dev_langs:
- C++
helpviewer_keywords:
- replace function [STL/CLR]
ms.assetid: 3792abca-8d73-476a-8540-c5f739aa48c2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 7a81bab1fbe77a7fc313e14d8d356abdd480f074
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33163493"
---
# <a name="replace-stlclr"></a>replace (STL/CLR)
Examina cada elemento de un intervalo y lo reemplaza si coincide con un valor especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<class _FwdIt, class _Ty> inline  
    void replace(_FwdIt _First, _FwdIt _Last,  
        const _Ty% _Oldval, const _Ty% _Newval);  
```  
  
## <a name="remarks"></a>Comentarios  
 Esta función comporta igual que la función de la biblioteca estándar de C++ `replace`. Para obtener más información, consulte [reemplazar](../standard-library/algorithm-functions.md#replace).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/algoritmo >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)