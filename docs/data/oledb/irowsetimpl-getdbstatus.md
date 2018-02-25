---
title: 'IRowsetImpl:: GetDBStatus | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- GetDBStatus
- IRowsetImpl.GetDBStatus
- IRowsetImpl::GetDBStatus
dev_langs:
- C++
helpviewer_keywords:
- GetDBStatus method
ms.assetid: e51d8ee2-fc0c-4909-861c-026c94fb0dfc
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6da72a2e93278fceb4ba43346ec8233752a8e1ac
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="irowsetimplgetdbstatus"></a>IRowsetImpl::GetDBStatus
Devuelve el `DBSTATUS` marcas de estado para el campo especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
      virtual DBSTATUS GetDBStatus(RowClass* currentRow,  
   ATLCOLUMNINFO* columnNames);  
```  
  
#### <a name="parameters"></a>Parámetros  
 [in] `currentRow`  
 La fila actual.  
  
 [in] `columnNames`  
 La columna para la que se solicita el estado.  
  
## <a name="return-value"></a>Valor devuelto  
 El [DBSTATUS](https://msdn.microsoft.com/en-us/library/ms722617.aspx) marcas para la columna.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [IRowsetImpl (Clase)](../../data/oledb/irowsetimpl-class.md)