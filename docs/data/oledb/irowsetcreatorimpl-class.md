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
ms.openlocfilehash: a53cd653258980d21e9dd297ae61c458732b7250
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210553"
---
# <a name="irowsetcreatorimpl-class"></a>IRowsetCreatorImpl (Clase)

Realiza las mismas funciones que `IObjectWithSite` pero también habilita las propiedades OLE DB `DBPROPCANSCROLLBACKWARDS DBPROPCANFETCHBACKWARDS`.

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

## <a name="members"></a>Members

### <a name="methods"></a>Métodos

|||
|-|-|
|[SetSite](#setsite)|Establece el sitio que contiene el objeto de conjunto de filas.|

## <a name="remarks"></a>Observaciones

Esta clase hereda de [IObjectWithSite](/windows/win32/api/ocidl/nn-ocidl-iobjectwithsite) e invalida [IObjectWithSite:: SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite). Cuando un comando de proveedor o un objeto de sesión crea un conjunto de filas, llama a `QueryInterface` en el objeto de conjunto de filas que busca `IObjectWithSite` y llama a `SetSite` pasar la interfaz de `IUnkown` del objeto de conjunto de filas como la interfaz de sitio.

## <a name="irowsetcreatorimplsetsite"></a><a name="setsite"></a>Irowsetcreatorimpl (:: SetSite

Establece el sitio que contiene el objeto de conjunto de filas. Para obtener más información, vea [IObjectWithSite:: SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite).

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(SetSite )(IUnknown* pCreator);
```

#### <a name="parameters"></a>Parámetros

*pCreator*<br/>
de Puntero al puntero de interfaz de `IUnknown` del sitio que administra el objeto de conjunto de filas.

### <a name="return-value"></a>Valor devuelto

HRESULT estándar.

### <a name="remarks"></a>Observaciones

Además, `IRowsetCreatorImpl::SetSite` habilita las propiedades de `DBPROPCANSCROLLBACKWARDS DBPROPCANFETCHBACKWARDS` de OLE DB.

## <a name="see-also"></a>Consulte también

[Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
