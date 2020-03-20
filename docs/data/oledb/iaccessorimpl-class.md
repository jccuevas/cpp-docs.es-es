---
title: IAccessorImpl (Clase)
ms.date: 11/04/2016
f1_keywords:
- IAccessorImpl
- ATL.IAccessorImpl.IAccessorImpl
- ATL::IAccessorImpl::IAccessorImpl
- IAccessorImpl::IAccessorImpl
- IAccessorImpl.IAccessorImpl
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
ms.openlocfilehash: f1865089100ac7f60e8c011e72eedb3d0a3f8470
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79545994"
---
# <a name="iaccessorimpl-class"></a>IAccessorImpl (Clase)

Proporciona una implementación de la interfaz [IAccessor](/previous-versions/windows/desktop/ms719672(v=vs.85)) .

## <a name="syntax"></a>Sintaxis

```cpp
template <class T,
   class BindType = ATLBINDINGS,
   class BindingVector = CAtlMap <HACCESSOR hAccessor, BindType* pBindingsStructure>>
class ATL_NO_VTABLE IAccessorImpl : public IAccessorImplBase<BindType>
```

### <a name="parameters"></a>Parámetros

*T*<br/>
La clase de objeto de conjunto de filas o de comando.

*BindType*<br/>
Unidad de almacenamiento para la información de enlace. El valor predeterminado es la estructura de `ATLBINDINGS` (vea atldb. h).

*BindingVector*<br/>
Unidad de almacenamiento para la información de columna. El valor predeterminado es [CAtlMap](../../atl/reference/catlmap-class.md) , donde el elemento clave es un valor de HACCESSOR y el elemento de valor es un puntero a una estructura de `BindType`.

## <a name="requirements"></a>Requisitos

**Encabezado:** atldb.h

## <a name="members"></a>Members

### <a name="methods"></a>Métodos

|||
|-|-|
|[IAccessorImpl](#iaccessorimpl)|El constructor.|

### <a name="interface-methods"></a>Métodos de interfaz

|||
|-|-|
|[AddRefAccessor](#addrefaccessor)|Agrega un contador de referencias a un descriptor de acceso existente.|
|[CreateAccessor](#createaccessor)|Crea un descriptor de acceso a partir de un conjunto de enlaces.|
|[GetBindings](#getbindings)|Devuelve los enlaces de un descriptor de acceso.|
|[ReleaseAccessor](#releaseaccessor)|Libera un descriptor de acceso.|

## <a name="remarks"></a>Observaciones

Esto es obligatorio en conjuntos de filas y comandos. OLE DB requiere que los proveedores implementen un HACCESSOR, que es una etiqueta para una matriz de estructuras [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) . Los HACCESSORs proporcionados por `IAccessorImpl` son direcciones de las estructuras de `BindType`. De forma predeterminada, `BindType` se define como un `ATLBINDINGS` en la definición de plantilla de `IAccessorImpl`. `BindType` proporciona un mecanismo utilizado por `IAccessorImpl` para realizar el seguimiento del número de elementos de su matriz de `DBBINDING`, así como un recuento de referencias y marcas de descriptor de acceso.

## <a name="iaccessorimpliaccessorimpl"></a><a name="iaccessorimpl"></a>IAccessorImpl:: IAccessorImpl

El constructor.

### <a name="syntax"></a>Sintaxis

```cpp
IAccessorImpl();
```

## <a name="iaccessorimpladdrefaccessor"></a><a name="addrefaccessor"></a>IAccessorImpl:: AddRefAccessor

Agrega un contador de referencias a un descriptor de acceso existente.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(AddRefAccessor)(HACCESSOR hAccessor,
   DBREFCOUNT* pcRefCount);
```

#### <a name="parameters"></a>Parámetros

Vea [IAccessor:: AddRefAccessor](/previous-versions/windows/desktop/ms714978(v=vs.85)) en la *Referencia del programador de OLE DB*.

## <a name="iaccessorimplcreateaccessor"></a><a name="createaccessor"></a>IAccessorImpl:: CreateAccessor

Crea un descriptor de acceso a partir de un conjunto de enlaces.

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

Vea [IAccessor:: CreateAccessor](/previous-versions/windows/desktop/ms720969(v=vs.85)) en la *Referencia del programador de OLE DB*.

## <a name="iaccessorimplgetbindings"></a><a name="getbindings"></a>IAccessorImpl:: GetBindings

Devuelve los enlaces de columnas básicas del consumidor en un descriptor de acceso.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(GetBindings)(HACCESSOR hAccessor,
   DBACCESSORFLAGS* pdwAccessorFlags,
   DBCOUNTITEM* pcBindings,
   DBBINDING** prgBindings);
```

#### <a name="parameters"></a>Parámetros

Vea [IAccessor:: GetBindings](/previous-versions/windows/desktop/ms721253(v=vs.85)) en la *Referencia del programador de OLE DB*.

## <a name="iaccessorimplreleaseaccessor"></a><a name="releaseaccessor"></a>IAccessorImpl:: ReleaseAccessor

Libera un descriptor de acceso.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(ReleaseAccessor)(HACCESSOR hAccessor,
   DBREFCOUNT* pcRefCount);
```

#### <a name="parameters"></a>Parámetros

Vea [IAccessor:: ReleaseAccessor](/previous-versions/windows/desktop/ms719717(v=vs.85)) en la *Referencia del programador de OLE DB*.

## <a name="see-also"></a>Consulte también

[Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)