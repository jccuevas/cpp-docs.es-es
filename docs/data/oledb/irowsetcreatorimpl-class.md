---
title: IRowsetCreatorImpl (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- IRowsetCreatorImpl class
- SetSite method
ms.assetid: 92cc950f-7978-4754-8d9a-defa63867d82
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 51534ffb027e35bbab5a9473cf4190c14b384808
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118158"
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

## <a name="setsite"></a> IRowsetCreatorImpl:: SetSite

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