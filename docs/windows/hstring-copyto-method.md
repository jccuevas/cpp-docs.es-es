---
title: "Hstring:: CopyTo (método) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
ms.assetid: a1fd2ef0-e175-4c18-927b-550e02a89e43
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1b49031359c2a51f6bdc28c52fb38ca4e29cb3e4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
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