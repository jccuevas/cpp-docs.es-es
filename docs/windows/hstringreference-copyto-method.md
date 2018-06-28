---
title: 'Hstringreference:: CopyTo (método) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: 179d9b14-1ced-4b16-b297-19ca1e92a462
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f65c08cad438328eb1a0e15495774dbde6845f4d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33874712"
---
# <a name="hstringreferencecopyto-method"></a>HStringReference::CopyTo (Método)
Copia el HStringReference actual objeto a un objeto HSTRING.  
  
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
 [HStringReference (clase)](../windows/hstringreference-class.md)