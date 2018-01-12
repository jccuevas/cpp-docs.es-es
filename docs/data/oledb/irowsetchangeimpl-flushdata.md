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
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 565b971b53ddb0a50b276d76aaaf62e9f7fa39f1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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