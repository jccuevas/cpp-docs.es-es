---
title: 'IRowsetUpdateImpl:: IsUpdateAllowed | Documentos de Microsoft'
ms.custom: ''
ms.date: 06/25/2018
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IRowsetUpdateImpl::IsUpdateAllowed
- IRowsetUpdateImpl.IsUpdateAllowed
- IsUpdateAllowed
dev_langs:
- C++
helpviewer_keywords:
- IsUpdateAllowed method
ms.assetid: d6daf3b3-a8e0-4275-a67d-897dea01e297
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 363626cedddea3da57e829a43c21c63b5c2b05cd
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/29/2018
ms.locfileid: "37122009"
---
# <a name="irowsetupdateimplisupdateallowed"></a>IRowsetUpdateImpl::IsUpdateAllowed
Invalide este método para comprobar si la seguridad, la integridad, y así sucesivamente antes de las actualizaciones.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT IsUpdateAllowed(DBPENDINGSTATUS /* [in] */ /* status */,  
   HROW /* [in] */ /* hRowUpdate */,  
   DBROWSTATUS* /* [out] */ /* pRowStatus */);  
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