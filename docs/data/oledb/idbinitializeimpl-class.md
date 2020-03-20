---
title: IDBInitializeImpl (Clase)
ms.date: 11/04/2016
f1_keywords:
- ATL.IDBInitializeImpl<T>
- ATL::IDBInitializeImpl<T>
- IDBInitializeImpl
- ATL::IDBInitializeImpl
- ATL.IDBInitializeImpl
- IDBInitializeImpl.IDBInitializeImpl
- IDBInitializeImpl::IDBInitializeImpl
- Initialize
- IDBInitializeImpl::Initialize
- IDBInitializeImpl.Initialize
- IDBInitializeImpl.Uninitialize
- Uninitialize
- IDBInitializeImpl::Uninitialize
- ATL::IDBInitializeImpl::m_dwStatus
- IDBInitializeImpl.m_dwStatus
- ATL.IDBInitializeImpl.m_dwStatus
- IDBInitializeImpl::m_dwStatus
- IDBInitializeImpl<T>::m_dwStatus
- ATL.IDBInitializeImpl<T>.m_dwStatus
- ATL::IDBInitializeImpl<T>::m_dwStatus
- m_dwStatus
- ATL::IDBInitializeImpl<T>::m_pCUtlPropInfo
- m_pCUtlPropInfo
- IDBInitializeImpl::m_pCUtlPropInfo
- ATL.IDBInitializeImpl.m_pCUtlPropInfo
- IDBInitializeImpl<T>::m_pCUtlPropInfo
- IDBInitializeImpl.m_pCUtlPropInfo
- ATL::IDBInitializeImpl::m_pCUtlPropInfo
helpviewer_keywords:
- IDBInitializeImpl class
- IDBInitializeImpl constructor
- Initialize method
- Uninitialize method
- m_dwStatus
- m_pCUtlPropInfo
ms.assetid: e4182f81-0443-44f5-a0d3-e7e075d6f883
ms.openlocfilehash: 1fc60db6db341d0667e24a81ae0f1394f54497ff
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79546066"
---
# <a name="idbinitializeimpl-class"></a>IDBInitializeImpl (Clase)

Proporciona una implementación para la interfaz [IDBInitialize](/previous-versions/windows/desktop/ms713706(v=vs.85)) .

## <a name="syntax"></a>Sintaxis

```cpp
template <class T>
class ATL_NO_VTABLE IDBInitializeImpl : public IDBInitialize
```

### <a name="parameters"></a>Parámetros

*T*<br/>
La clase, derivada de `IDBInitializeImpl`.

## <a name="requirements"></a>Requisitos

**Encabezado:** atldb.h

## <a name="members"></a>Members

### <a name="methods"></a>Métodos

|||
|-|-|
|[IDBInitializeImpl](#idbinitializeimpl)|El constructor.|

### <a name="interface-methods"></a>Métodos de interfaz

|||
|-|-|
|[Initialize](#initialize)|Inicia el proveedor.|
|[Anular](#uninitialize)|Detiene el proveedor.|

### <a name="data-members"></a>Miembros de datos

|||
|-|-|
|[m_dwStatus](#dwstatus)|Marcas de origen de datos.|
|[m_pCUtlPropInfo](#pcutlpropinfo)|Un puntero a la implementación de la información de propiedades de la base de datos.|

## <a name="remarks"></a>Observaciones

Una interfaz obligatoria en los objetos de origen de datos y la interfaz opcional en los enumeradores.

## <a name="idbinitializeimplidbinitializeimpl"></a><a name="idbinitializeimpl"></a>IDBInitializeImpl:: IDBInitializeImpl

El constructor.

### <a name="syntax"></a>Sintaxis

```cpp
IDBInitializeImpl();
```

### <a name="remarks"></a>Observaciones

Inicializa todos los miembros de datos.

## <a name="idbinitializeimplinitialize"></a><a name="initialize"></a>IDBInitializeImpl:: Initialize

Inicializa el objeto de origen de datos mediante la preparación de su compatibilidad con la propiedad.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(Initialize)(void);
```

### <a name="remarks"></a>Observaciones

Vea [IDBInitialize:: Initialize](/previous-versions/windows/desktop/ms718026(v=vs.85)) en la *Referencia del programador de OLE DB*.

## <a name="idbinitializeimpluninitialize"></a><a name="uninitialize"></a>IDBInitializeImpl:: UnInitialize

Coloca el objeto de origen de datos en un estado no inicializado liberando los recursos internos, como la compatibilidad con las propiedades.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(Uninitialize)(void);
```

### <a name="remarks"></a>Observaciones

Vea [IDBInitialize:: UnInitialize](/previous-versions/windows/desktop/ms719648(v=vs.85)) en la *Referencia del programador de OLE DB*.

## <a name="idbinitializeimplm_dwstatus"></a><a name="dwstatus"></a>IDBInitializeImpl:: m_dwStatus

Marcas de origen de datos.

### <a name="syntax"></a>Sintaxis

```cpp
DWORD m_dwStatus;
```

### <a name="remarks"></a>Observaciones

Estas marcas especifican o indican el estado de varios atributos para el objeto de origen de datos. Contiene uno o varios de los siguientes valores de **enumeración** :

```cpp
enum DATASOURCE_FLAGS {
    DSF_MASK_INIT     = 0xFFFFF00F,
    DSF_PERSIST_DIRTY = 0x00000001,
    DSF_INITIALIZED   = 0x00000010,
};
```

|||
|-|-|
|`DSF_MASK_INIT`|Máscara para habilitar la restauración del estado no inicializado.|
|`DSF_PERSIST_DIRTY`|Establezca si el objeto de origen de datos requiere persistencia (es decir, si se ha producido algún cambio).|
|`DSF_INITIALIZED`|Se establece si el origen de datos se ha inicializado.|

## <a name="idbinitializeimplm_pcutlpropinfo"></a><a name="pcutlpropinfo"></a>IDBInitializeImpl:: m_pCUtlPropInfo

Un puntero a un objeto de implementación para la información de propiedades de la base de datos.

### <a name="syntax"></a>Sintaxis

```cpp
CUtlPropInfo< T >* m_pCUtlPropInfo;
```

## <a name="see-also"></a>Consulte también

[Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)