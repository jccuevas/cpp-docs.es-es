---
title: IRowsetCreatorImpl (Clase)
ms.date: 11/04/2016
f1_keywords:
- ATL::IRowsetCreatorImpl
- ATL.IRowsetCreatorImpl
- ATL::IRowsetCreatorImpl<T>
- ATL.IRowsetCreatorImpl<T>
- IRowsetCreatorImpl
- IRowsetCreatorImpl.SetSite
- IRowsetCreatorImpl<T>::SetSite
- IRowsetCreatorImpl::SetSite
- SetSite
- ATL.IRowsetCreatorImpl.SetSite
- ATL::IRowsetCreatorImpl<T>::SetSite
- ATL::IRowsetCreatorImpl::SetSite
- ATL.IRowsetCreatorImpl<T>.SetSite
helpviewer_keywords:
- IRowsetCreatorImpl class
- SetSite method
ms.assetid: 92cc950f-7978-4754-8d9a-defa63867d82
ms.openlocfilehash: 3dc5cb06b3eb7f01667e4e1ec09dd60f9befae77
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59026609"
---
# <a name="irowsetcreatorimpl-class"></a>IRowsetCreatorImpl (Clase)

Realiza las mismas funciones que `IObjectWithSite` , pero también permite que las propiedades de OLE DB `DBPROPCANSCROLLBACKWARDS DBPROPCANFETCHBACKWARDS`.

## <a name="syntax"></a>Sintaxis

```cpp
template < class T >
class ATL_NO_VTABLE IRowsetCreatorImpl
   : public IObjectWithSiteImpl< T >
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Una clase derivada de `IRowsetCreator`.

## <a name="requirements"></a>Requisitos

**Encabezado:** atldb.h

## <a name="members"></a>Miembros

### <a name="methods"></a>Métodos

|||
|-|-|
|[SetSite](#setsite)|Establece el sitio que contiene el objeto de conjunto de filas.|

## <a name="remarks"></a>Comentarios

Esta clase hereda de [IObjectWithSite](/windows/desktop/api/ocidl/nn-ocidl-iobjectwithsite) e invalida [IObjectWithSite::SetSite](/windows/desktop/api/ocidl/nf-ocidl-iobjectwithsite-setsite). Cuando un objeto de comando o sesión de proveedor crea un conjunto de filas, llama a `QueryInterface` en el objeto de conjunto de filas buscando `IObjectWithSite` y llama a `SetSite` pasando el objeto de conjunto de filas `IUnkown` interfaz como la interfaz de sitio.

## <a name="setsite"></a> IRowsetCreatorImpl::SetSite

Establece el sitio que contiene el objeto de conjunto de filas. Para obtener más información, consulte [IObjectWithSite::SetSite](/windows/desktop/api/ocidl/nf-ocidl-iobjectwithsite-setsite).

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(SetSite )(IUnknown* pCreator);
```

#### <a name="parameters"></a>Parámetros

*pCreator*<br/>
[in] Puntero a la `IUnknown` puntero de interfaz del sitio de administración en el objeto de conjunto de filas.

### <a name="return-value"></a>Valor devuelto

Un HRESULT estándar.

### <a name="remarks"></a>Comentarios

Además, `IRowsetCreatorImpl::SetSite` permite OLE DB `DBPROPCANSCROLLBACKWARDS DBPROPCANFETCHBACKWARDS` propiedades.

## <a name="see-also"></a>Vea también

[Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)