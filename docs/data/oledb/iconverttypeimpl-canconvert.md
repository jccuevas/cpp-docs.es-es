---
title: 'Iconverttypeimpl:: CanConvert | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IConvertTypeImpl.CanConvert
- CanConvert
- IConvertTypeImpl::CanConvert
dev_langs:
- C++
helpviewer_keywords:
- CanConvert method
ms.assetid: bdad6e95-bc0b-4427-9b5e-eea51f09f392
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 47b1d5ddf0d5ad3cba1745767bfe82256a39cdd8
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
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