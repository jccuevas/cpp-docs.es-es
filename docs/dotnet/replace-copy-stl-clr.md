---
title: replace_copy (STL/CLR) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::replace_copy
dev_langs:
- C++
helpviewer_keywords:
- replace_copy function [STL/CLR]
ms.assetid: b531b49b-b16d-4b04-8f80-74f43dd496a4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a027bbf1374988d79b94585f0d303c7e352ddbee
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="replacecopy-stlclr"></a>replace_copy (STL/CLR)
Examina cada elemento de un intervalo de origen y lo reemplaza si coincide con un valor especificado y copia el resultado a un nuevo intervalo de destino.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<class _InIt, class _OutIt, class _Ty> inline  
    _OutIt replace_copy(_InIt _First, _InIt _Last, _OutIt _Dest,  
        const _Ty% _Oldval, const _Ty% _Newval);  
```  
  
## <a name="remarks"></a>Comentarios  
 Esta función comporta igual que la función de la biblioteca estándar de C++ `replace_copy`. Para obtener más información, consulte [replace_copy](../standard-library/algorithm-functions.md#replace_copy).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/algoritmo >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)