---
title: IAccessorImpl (Clase)
ms.date: 11/04/2016
f1_keywords:
- IAccessorImpl
- ATL.IAccessorImpl.IAccessorImpl
- ATL::IAccessorImpl::IAccessorImpl
- IAccessorImpl::IAccessorImpl
- IAccessorImpl.IAccessorImpl
- IAccessorImpl
- ATL::IAccessorImpl::AddRefAccessor
- AddRefAccessor
- IAccessorImpl::AddRefAccessor
- IAccessorImpl.AddRefAccessor
- ATL.IAccessorImpl.AddRefAccessor
- IAccessorImpl::CreateAccessor
- CreateAccessor
- ATL::IAccessorImpl::CreateAccessor
- IAccessorImpl.CreateAccessor
- ATL.IAccessorImpl.CreateAccessor
- IAccessorImpl.GetBindings
- ATL::IAccessorImpl::GetBindings
- IAccessorImpl::GetBindings
- GetBindings
- ATL.IAccessorImpl.GetBindings
- ReleaseAccessor
- IAccessorImpl::ReleaseAccessor
- ATL.IAccessorImpl.ReleaseAccessor
- ATL::IAccessorImpl::ReleaseAccessor
- IAccessorImpl.ReleaseAccessor
helpviewer_keywords:
- IAccessorImpl class
- IAccessorImpl class, constructor
- IAccessorImpl constructor
- AddRefAccessor method
- CreateAccessor method
- GetBindings method
- ReleaseAccessor method
ms.assetid: 768606da-8b71-417c-a62c-88069ce7730d
ms.openlocfilehash: a4f98cdfea9ea1e82ec0a3de09e292604a6c199f
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59032120"
---
# <a name="iaccessorimpl-class"></a>IAccessorImpl (Clase)

Proporciona una implementación de la [IAccessor](/previous-versions/windows/desktop/ms719672(v=vs.85)) interfaz.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T,
   class BindType = ATLBINDINGS,
   class BindingVector = CAtlMap <HACCESSOR hAccessor, BindType* pBindingsStructure>>
class ATL_NO_VTABLE IAccessorImpl : public IAccessorImplBase<BindType>
```

### <a name="parameters"></a>Parámetros

*T*<br/>
La clase de objeto de conjunto de filas o un comando.

*BindType*<br/>
Unidad de almacenamiento de información de enlace. El valor predeterminado es el `ATLBINDINGS` estructura (consulte atldb.h).

*BindingVector*<br/>
Unidad de almacenamiento para obtener información de columna. El valor predeterminado es [CAtlMap](../../atl/reference/catlmap-class.md) donde el elemento clave es un valor HACCESSOR y el elemento de valor es un puntero a un `BindType` estructura.

## <a name="requirements"></a>Requisitos

**Encabezado:** atldb.h

## <a name="members"></a>Miembros

### <a name="methods"></a>Métodos

|||
|-|-|
|[IAccessorImpl](#iaccessorimpl)|El constructor.|

### <a name="interface-methods"></a>Métodos de interfaz

|||
|-|-|
|[AddRefAccessor](#addrefaccessor)|Agrega un recuento de referencias a un descriptor de acceso existente.|
|[CreateAccessor](#createaccessor)|Crea un descriptor de acceso de un conjunto de enlaces.|
|[GetBindings](#getbindings)|Devuelve los enlaces de un descriptor de acceso.|
|[ReleaseAccessor](#releaseaccessor)|Libera un descriptor de acceso.|

## <a name="remarks"></a>Comentarios

Esto es obligatorio en los conjuntos de filas y los comandos. OLE DB requiere que los proveedores implementar un HACCESSOR, que es una etiqueta a una matriz de [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) estructuras. HACCESSORs proporcionadas por `IAccessorImpl` son direcciones de la `BindType` estructuras. De forma predeterminada, `BindType` se define como un `ATLBINDINGS` en `IAccessorImpl`de definición de plantilla. `BindType` Proporciona un mecanismo que utiliza `IAccessorImpl` para realizar un seguimiento del número de elementos de su `DBBINDING` de matriz, así como un indicadores de descriptores de acceso y el recuento de referencia.

## <a name="iaccessorimpl"></a> IAccessorImpl::IAccessorImpl

El constructor.

### <a name="syntax"></a>Sintaxis

```cpp
IAccessorImpl();
```

## <a name="addrefaccessor"></a> IAccessorImpl::AddRefAccessor

Agrega un recuento de referencias a un descriptor de acceso existente.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(AddRefAccessor)(HACCESSOR hAccessor,
   DBREFCOUNT* pcRefCount);
```

#### <a name="parameters"></a>Parámetros

Consulte [IAccessor::AddRefAccessor](/previous-versions/windows/desktop/ms714978(v=vs.85)) en el *referencia del programador OLE DB*.

## <a name="createaccessor"></a> IAccessorImpl::CreateAccessor

Crea un descriptor de acceso de un conjunto de enlaces.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(CreateAccessor)(DBACCESSORFLAGS dwAccessorFlags,
   DBCOUNTITEM cBindings,
   const DBBINDING rgBindings[],
   DBLENGTH cbRowSize,
   HACCESSOR* phAccessor,
   DBBINDSTATUS rgStatus[]);
```

#### <a name="parameters"></a>Parámetros

Consulte [IAccessor:: CreateAccessor](/previous-versions/windows/desktop/ms720969(v=vs.85)) en el *referencia del programador OLE DB*.

## <a name="getbindings"></a> IAccessorImpl::GetBindings

Devuelve los enlaces de columnas básicas del consumidor en un descriptor de acceso.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(GetBindings)(HACCESSOR hAccessor,
   DBACCESSORFLAGS* pdwAccessorFlags,
   DBCOUNTITEM* pcBindings,
   DBBINDING** prgBindings);
```

#### <a name="parameters"></a>Parámetros

Consulte [IAccessor::GetBindings](/previous-versions/windows/desktop/ms721253(v=vs.85)) en el *referencia del programador OLE DB*.

## <a name="releaseaccessor"></a> IAccessorImpl::ReleaseAccessor

Libera un descriptor de acceso.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(ReleaseAccessor)(HACCESSOR hAccessor,
   DBREFCOUNT* pcRefCount);
```

#### <a name="parameters"></a>Parámetros

Consulte [IAccessor:: ReleaseAccessor](/previous-versions/windows/desktop/ms719717(v=vs.85)) en el *referencia del programador OLE DB*.

## <a name="see-also"></a>Vea también

[Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)