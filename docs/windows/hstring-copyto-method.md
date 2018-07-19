---
title: 'Hstring:: CopyTo (método) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: a1fd2ef0-e175-4c18-927b-550e02a89e43
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b44974faf5fc1f068d28d7febe3ed2a266f4869e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33874777"
---
# <a name="hstringcopyto-method"></a>HString::CopyTo (Método)
Copia el HString actual objeto a un objeto HSTRING.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
HRESULT CopyTo(  
   _Out_ HSTRING *str  
   ) const throw();  
```  
  
#### <a name="parameters"></a>Parámetros  
 `str`  
 El HSTRING que recibe la copia.  
  
## <a name="remarks"></a>Comentarios  
 Este método llama a la [WindowsDuplicateString](http://msdn.microsoft.com/library/br224634.aspx) (función).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers  
  
## <a name="see-also"></a>Vea también  
 [HString (clase)](../windows/hstring-class.md)