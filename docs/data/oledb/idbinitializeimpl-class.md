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
- IDBInitializeImpl
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
ms.openlocfilehash: 3418ce11e1a607d66fee593b32fd3a4b7d197407
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59033987"
---
# <a name="idbinitializeimpl-class"></a>IDBInitializeImpl (Clase)

Proporciona una implementación para el [IDBInitialize](/previous-versions/windows/desktop/ms713706(v=vs.85)) interfaz.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T>
class ATL_NO_VTABLE IDBInitializeImpl : public IDBInitialize
```

### <a name="parameters"></a>Parámetros

*T*<br/>
La clase derivada de `IDBInitializeImpl`.

## <a name="requirements"></a>Requisitos

**Encabezado:** atldb.h

## <a name="members"></a>Miembros

### <a name="methods"></a>Métodos

|||
|-|-|
|[IDBInitializeImpl](#idbinitializeimpl)|El constructor.|

### <a name="interface-methods"></a>Métodos de interfaz

|||
|-|-|
|[Initialize](#initialize)|Inicia el proveedor.|
|[Uninitialize](#uninitialize)|Detiene el proveedor.|

### <a name="data-members"></a>Miembros de datos

|||
|-|-|
|[m_dwStatus](#dwstatus)|Indicadores del origen de datos.|
|[m_pCUtlPropInfo](#pcutlpropinfo)|Un puntero a la implementación de la información de las propiedades de la base de datos.|

## <a name="remarks"></a>Comentarios

Una interfaz obligatoria en los objetos de origen de datos y una interfaz opcional sobre los enumeradores.

## <a name="idbinitializeimpl"></a> IDBInitializeImpl::IDBInitializeImpl

El constructor.

### <a name="syntax"></a>Sintaxis

```cpp
IDBInitializeImpl();
```

### <a name="remarks"></a>Comentarios

Inicializa a todos los miembros de datos.

## <a name="initialize"></a> IDBInitializeImpl::Initialize

Inicializa el objeto de origen de datos mediante la preparación de su compatibilidad con la propiedad.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(Initialize)(void);
```

### <a name="remarks"></a>Comentarios

Consulte [IDBInitialize:: Initialize](/previous-versions/windows/desktop/ms718026(v=vs.85)) en el *referencia del programador OLE DB*.

## <a name="uninitialize"></a> IDBInitializeImpl::Uninitialize

Coloca los datos del origen de objeto en un estado no inicializado al liberar los recursos internos, como la compatibilidad con la propiedad.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(Uninitialize)(void);
```

### <a name="remarks"></a>Comentarios

Consulte [IDBInitialize:: UnInitialize](/previous-versions/windows/desktop/ms719648(v=vs.85)) en el *referencia del programador OLE DB*.

## <a name="dwstatus"></a> IDBInitializeImpl::m_dwStatus

Indicadores del origen de datos.

### <a name="syntax"></a>Sintaxis

```cpp
DWORD m_dwStatus;
```

### <a name="remarks"></a>Comentarios

Estas marcas especifican o indican el estado de varios atributos para el objeto de origen de datos. Contiene uno o varios de los siguientes **enum** valores:

```cpp
enum DATASOURCE_FLAGS {
    DSF_MASK_INIT     = 0xFFFFF00F,
    DSF_PERSIST_DIRTY = 0x00000001,
    DSF_INITIALIZED   = 0x00000010,
};
```

|||
|-|-|
|`DSF_MASK_INIT`|Una máscara para habilitar la restauración de estado no inicializado.|
|`DSF_PERSIST_DIRTY`|Establece si el objeto de origen de datos requiere la persistencia (es decir, si ha habido cambios).|
|`DSF_INITIALIZED`|Establecer si se ha inicializado el origen de datos.|

## <a name="pcutlpropinfo"></a> IDBInitializeImpl::m_pCUtlPropInfo

Un puntero al objeto de implementación para la información de las propiedades de la base de datos.

### <a name="syntax"></a>Sintaxis

```cpp
CUtlPropInfo< T >* m_pCUtlPropInfo;
```

## <a name="see-also"></a>Vea también

[Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)