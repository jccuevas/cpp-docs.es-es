---
title: IRowsetIdentityImpl (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::IRowsetIdentityImpl
- ATL.IRowsetIdentityImpl
- IRowsetIdentityImpl
- IsSameRow
- IRowsetIdentityImpl.IsSameRow
- ATL.IRowsetIdentityImpl.IsSameRow
- IRowsetIdentityImpl::IsSameRow
- ATL::IRowsetIdentityImpl::IsSameRow
dev_langs:
- C++
helpviewer_keywords:
- IRowsetIdentityImpl class
- IsSameRow method
ms.assetid: 56821edf-e045-40c8-96bd-231552cd5799
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ed8cc8fc2b61a3a85beb7297317c5b266557268c
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/14/2018
ms.locfileid: "42571510"
---
# <a name="irowsetidentityimpl-class"></a>IRowsetIdentityImpl (Clase)
Implementa OLE DB [IRowsetIdentity](/previous-versions/windows/desktop/ms715913\(v=vs.85\)) interfaz, que permite realizar pruebas para la identidad de fila.  
  
## <a name="syntax"></a>Sintaxis

```cpp
template <class T, class RowClass = CSimpleRow>  
class ATL_NO_VTABLE IRowsetIdentityImpl   
   : public IRowsetIdentity  
```  
  
### <a name="parameters"></a>Parámetros  
 *T*  
 Una clase derivada de `IRowsetIdentityImpl`.  
  
 *RowClass*  
 La unidad de almacenamiento para el `HROW`.  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="members"></a>Miembros  
  
### <a name="methods"></a>Métodos  
  
|||  
|-|-|  
|[IsSameRow](#issamerow)|Compara dos identificadores de fila para ver si hacen referencia a la misma fila.|  
  
## <a name="issamerow"></a> Irowsetidentityimpl:: Issamerow
Compara dos identificadores de fila para ver si hacen referencia a la misma fila.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
STDMETHOD(IsSameRow )(HROW hThisRow,  
   HROW hThatRow);  
```  
  
#### <a name="parameters"></a>Parámetros  
 Consulte [IRowsetIdentity::IsSameRow](/previous-versions/windows/desktop/ms719629\(v=vs.85\)) en el *referencia del programador OLE DB*.  
  
### <a name="remarks"></a>Comentarios  
 Para comparar los identificadores de fila, este método convierte el `HROW` identificadores a `RowClass` miembros y las llamadas `memcmp` en los punteros.  
  
## <a name="see-also"></a>Vea también  
 [Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)