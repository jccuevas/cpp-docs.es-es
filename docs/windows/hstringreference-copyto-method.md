---
title: "Hstringreference:: CopyTo (método) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
ms.assetid: 179d9b14-1ced-4b16-b297-19ca1e92a462
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f93dd138490834451a665761f4c575a751bfe7ea
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
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