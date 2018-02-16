---
title: 'IRowsetUpdateImpl:: IsUpdateAllowed | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IRowsetUpdateImpl::IsUpdateAllowed
- IRowsetUpdateImpl.IsUpdateAllowed
- IsUpdateAllowed
dev_langs:
- C++
helpviewer_keywords:
- IsUpdateAllowed method
ms.assetid: d6daf3b3-a8e0-4275-a67d-897dea01e297
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4744e6f5be9c9b535c7359b615a5195c6da33fd9
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="irowsetupdateimplisupdateallowed"></a>IRowsetUpdateImpl::IsUpdateAllowed
Invalide este método para comprobar si la seguridad, la integridad, y así sucesivamente antes de las actualizaciones.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT IsUpdateAllowed(DBPENDINGSTATUS /* [in] *//* status */,  
   HROW /* [in] *//* hRowUpdate */,  
   DBROWSTATUS* /* [out] *//* pRowStatus */);  
```  
  
#### <a name="parameters"></a>Parámetros  
 *status*  
 [in] El estado de las operaciones pendientes de las filas.  
  
 *hRowUpdate*  
 [in] Identificador para las filas que el usuario desea actualizar.  
  
 *pRowStatus*  
 [out] El estado devuelto al usuario.  
  
## <a name="remarks"></a>Comentarios  
 Si determina que una actualización debe permitirse, devuelve `S_OK`; de lo contrario devuelve **E_FAIL**. Si permite que una actualización, también debe establecer el **DBROWSTATUS** en [IRowsetUpdateImpl:: Update](../../data/oledb/irowsetupdateimpl-update.md) a un correspondiente [estado de la fila](https://msdn.microsoft.com/en-us/library/ms722752.aspx).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [IRowsetUpdateImpl (Clase)](../../data/oledb/irowsetupdateimpl-class.md)