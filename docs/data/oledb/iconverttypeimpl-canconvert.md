---
title: 'Iconverttypeimpl:: CanConvert | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IConvertTypeImpl.CanConvert
- CanConvert
- IConvertTypeImpl::CanConvert
dev_langs:
- C++
helpviewer_keywords:
- CanConvert method
ms.assetid: bdad6e95-bc0b-4427-9b5e-eea51f09f392
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a2f7e32fd01c932f24b617951d601ddcfe7fb5af
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33099893"
---
# <a name="iconverttypeimplcanconvert"></a>IConvertTypeImpl::CanConvert
Proporciona información sobre la disponibilidad de las conversiones de tipos en un comando o en un conjunto de filas.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
      STDMETHOD(CanConvert)(DBTYPE wFromType,   
   DBTYPE wToType,   
   DBCONVERTFLAGS dwConvertFlags);  
```  
  
#### <a name="parameters"></a>Parámetros  
 Vea [IConvertType::CanConvert](https://msdn.microsoft.com/en-us/library/ms711224.aspx) en el *referencia del programador OLE DB*.  
  
## <a name="remarks"></a>Comentarios  
 Usa la conversión de datos de OLE DB en `MSADC.DLL`.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [IConvertTypeImpl (Clase)](../../data/oledb/iconverttypeimpl-class.md)