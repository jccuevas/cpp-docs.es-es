---
title: 'IRowsetChangeImpl:: FlushData | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IRowsetChangeImpl::FlushData
- IRowsetChangeImpl.FlushData
- FlushData
dev_langs: C++
helpviewer_keywords: FlushData method
ms.assetid: fd4bc73b-bc25-4aab-90d5-0bed92670c88
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 31555e1f8305a281955902b71fdc71fbcc5405e5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="irowsetchangeimplflushdata"></a>IRowsetChangeImpl::FlushData
Se reemplaza por proveedor para confirmar datos en su almacén.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      HRESULT FlushData(  
   HROW hRowToFlush,  
   HACCESSOR hAccessorToFlush   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 *hRowToFlush*  
 [in] Identificador de las filas de los datos. El tipo de esta fila se determina a partir del *RowClass* argumento de plantilla de la `IRowsetImpl` clase (`CSimpleRow` de forma predeterminada).  
  
 *hAccessorToFlush*  
 [in] Identificador de descriptor de acceso, que contiene información de enlace e información de tipo en su **PROVIDER_MAP** (consulte [IAccessorImpl](../../data/oledb/iaccessorimpl-class.md)).  
  
## <a name="return-value"></a>Valor devuelto  
 Un `HRESULT` estándar.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [IRowsetChangeImpl (Clase)](../../data/oledb/irowsetchangeimpl-class.md)