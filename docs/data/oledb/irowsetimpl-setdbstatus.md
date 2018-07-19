---
title: 'IRowsetImpl:: SetDBStatus | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IRowsetImpl.SetDBStatus
- IRowsetImpl::SetDBStatus
- SetDBStatus
dev_langs:
- C++
helpviewer_keywords:
- SetDBStatus method
ms.assetid: b73f526a-4fc6-4adb-9611-c3cca2cddb23
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7e6e07b6fe1a45a779c5ffe1e1afffaabdcb6d34
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33103907"
---
# <a name="irowsetimplsetdbstatus"></a>IRowsetImpl::SetDBStatus
Establece la `DBSTATUS` marcas de estado para el campo especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
      virtual HRESULT SetDBStatus(DBSTATUS* statusFlags,  
   RowClass* currentRow,  
   ATLCOLUMNINFO* columnInfo);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `statusFlags`  
 El [DBSTATUS](https://msdn.microsoft.com/en-us/library/ms722617.aspx) marcas para establecer para la columna.  
  
 `currentRow`  
 La fila actual.  
  
 *columnInfo*  
 La columna para la que se define el estado.  
  
## <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
## <a name="remarks"></a>Comentarios  
 El proveedor reemplaza esta función para proporcionar un procesamiento especial para **DBSTATUS_S_ISNULL** y **DBSTATUS_S_DEFAULT**.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [IRowsetImpl (Clase)](../../data/oledb/irowsetimpl-class.md)