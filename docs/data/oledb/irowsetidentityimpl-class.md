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
ms.openlocfilehash: 1431fb9b35ab83f6cb0fc167eff4ba4508f2e301
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46036194"
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

*T*<br/>
Una clase derivada de `IRowsetIdentityImpl`.  
  
*RowClass*<br/>
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

[Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)