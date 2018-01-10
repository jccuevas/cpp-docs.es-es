---
title: 'IRowsetImpl:: CreateRow | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IRowsetImpl.CreateRow
- ATL.IRowsetImpl.CreateRow
- ATL::IRowsetImpl::CreateRow
- CreateRow
- IRowsetImpl::CreateRow
dev_langs: C++
helpviewer_keywords: CreateRow method
ms.assetid: b01c430c-9484-4fef-a6cf-a2e8d9d99130
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f90a5de73b5eea37eea192a4886fe29d1d8b435b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="irowsetimplcreaterow"></a>IRowsetImpl::CreateRow
Un método auxiliar llamado por el método [GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md) para asignar un nuevo **HROW**.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      HRESULT CreateRow(  
   DBROWOFFSET lRowsOffset,  
   DBCOUNTITEM& cRowsObtained,  
   HROW* rgRows   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 *lRowsOffset*  
 Posición del cursor de la fila que se va a crear.  
  
 *cRowsObtained*  
 Pasa una referencia al usuario que indica el número de filas creadas.  
  
 *rgRows*  
 Una matriz de **HROW**s devuelve al llamador con los identificadores de fila recién creado.  
  
## <a name="remarks"></a>Comentarios  
 Si la fila no existe, este método llama a [AddRefRows](../../data/oledb/irowsetimpl-addrefrows.md) y devuelve. En caso contrario, asigna una nueva instancia de la variable de plantilla RowClass y lo agrega a [m_rgRowHandles](../../data/oledb/irowsetimpl-m-rgrowhandles.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [IRowsetImpl (Clase)](../../data/oledb/irowsetimpl-class.md)