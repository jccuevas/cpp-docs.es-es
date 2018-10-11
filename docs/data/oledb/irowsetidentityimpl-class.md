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
ms.openlocfilehash: b47cbf2b30323cf51881ebaae9f546001a2d61b3
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/11/2018
ms.locfileid: "49081505"
---
# <a name="irowsetidentityimpl-class"></a>IRowsetIdentityImpl (Clase)

Implementa OLE DB [IRowsetIdentity](/previous-versions/windows/desktop/ms715913) interfaz, que permite realizar pruebas para la identidad de fila.  
  
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

Consulte [IRowsetIdentity::IsSameRow](/previous-versions/windows/desktop/ms719629) en el *referencia del programador OLE DB*.  
  
### <a name="remarks"></a>Comentarios  

Para comparar los identificadores de fila, este método convierte el `HROW` identificadores a `RowClass` miembros y las llamadas `memcmp` en los punteros.  
  
## <a name="see-also"></a>Vea también  

[Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)