---
title: RuntimeClass (clase) | Microsoft Docs
ms.custom: ''
ms.date: 09/11/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClass
- implements/Microsoft::WRL::RuntimeClass::AddRef
- implements/Microsoft::WRL::RuntimeClass::DecrementReference
- implements/Microsoft::WRL::RuntimeClass::GetIids
- implements/Microsoft::WRL::RuntimeClass::GetRuntimeClassName
- implements/Microsoft::WRL::RuntimeClass::GetTrustLevel
- implements/Microsoft::WRL::RuntimeClass::GetWeakReference
- implements/Microsoft::WRL::RuntimeClass::InternalAddRef
- implements/Microsoft::WRL::RuntimeClass::QueryInterface
- implements/Microsoft::WRL::RuntimeClass::Release
- implements/Microsoft::WRL::RuntimeClass::RuntimeClass
- implements/Microsoft::WRL::RuntimeClass::~RuntimeClass
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::RuntimeClass class
- Microsoft::WRL::RuntimeClass::AddRef method
- Microsoft::WRL::RuntimeClass::DecrementReference method
- Microsoft::WRL::RuntimeClass::GetIids method
- Microsoft::WRL::RuntimeClass::GetRuntimeClassName method
- Microsoft::WRL::RuntimeClass::GetTrustLevel method
- Microsoft::WRL::RuntimeClass::GetWeakReference method
- Microsoft::WRL::RuntimeClass::InternalAddRef method
- Microsoft::WRL::RuntimeClass::QueryInterface method
- Microsoft::WRL::RuntimeClass::Release method
- Microsoft::WRL::RuntimeClass::RuntimeClass, constructor
- Microsoft::WRL::RuntimeClass::~RuntimeClass, destructor
ms.assetid: d52f9d1a-98e5-41f2-a143-8fb629dd0727
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: db9476e225b19f76fb695063c9c5058e8d9b2871
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50080031"
---
# <a name="runtimeclass-class"></a>RuntimeClass (Clase)

Representa una clase WinRT o COM que hereda las interfaces especificadas y proporciona el especificado en tiempo de ejecución de Windows, COM clásico y el soporte técnico de la referencia débil.

Esta clase proporciona la implementación de código reutilizable de clases COM y WinRT, que proporciona la implementación de `QueryInterface`, `AddRef`, `Release` etc., administra el recuento de referencias del módulo y tiene compatibilidad para proporcionar el generador de clases para objetos activables.

## <a name="syntax"></a>Sintaxis

```cpp
template <typename ...TInterfaces> class RuntimeClass
template <unsigned int classFlags, typename ...TInterfaces> class RuntimeClass;
```

### <a name="parameters"></a>Parámetros

*classFlags*<br/>
Parámetro opcional. Una combinación de uno o varios [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) valores de enumeración. El `__WRL_CONFIGURATION_LEGACY__` macros se pueden definir para cambiar el valor predeterminado de classFlags para todas las clases en tiempo de ejecución en el proyecto. Si ha definido, RuntimeClass instancias son no ágiles de forma predeterminada. Cuando no está definido, las instancias de RuntimeClass son ágiles de forma predeterminada. Para evitar la ambigüedad especifique siempre el `Microsoft::WRL::FtmBase` en `TInterfaces` o `RuntimeClassType::InhibitFtmBase`. Tenga en cuenta que si InhibitFtmBase y FtmBase son que ambos utilizan el objeto será ágil.

*TInterfaces*<br/>
La lista de interfaces que el objeto implementa más allá de `IUnknown`, `IInspectable` u otras interfaces controlados por [RuntimeClassType](../windows/runtimeclasstype-enumeration.md). También puede enumerar otras clases que se deriva, en particular `Microsoft::WRL::FtmBase` para hacer que el objeto agile y provocar que implemente `IMarshal`.

## <a name="members"></a>Miembros

`RuntimeClassInitialize`<br/>
Una función que inicializa el objeto si el `MakeAndInitialize` función de plantilla se usa para construir el objeto. Devuelve S_OK si el objeto se inicializó correctamente, o un código de error COM si no se pudo inicializar. El código de error COM se propaga como el valor devuelto de `MakeAndInitialize`. Tenga en cuenta que el `RuntimeClassInitialize` no se llama al método si el `Make` función de plantilla se usa para construir el objeto.

### <a name="public-constructors"></a>Constructores públicos

| Name                                               | Descripción                                                     |
| -------------------------------------------------- | --------------------------------------------------------------- |
| [Runtimeclass](#runtimeclass)        | Inicializa la instancia actual de la `RuntimeClass` clase.   |
| [RuntimeClass:: ~ RuntimeClass](#tilde-runtimeclass) | Desinicializa la instancia actual de la `RuntimeClass` clase. |

### <a name="public-methods"></a>Métodos públicos

| Name                                                      | Descripción                                                                                        |
| --------------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| [Runtimeclass](#addref)                           | Incrementa el recuento de referencias actual `RuntimeClass` objeto.                              |
| [Decrementreference](#decrementreference)   | Disminuye el recuento de referencias actual `RuntimeClass` objeto.                              |
| [Runtimeclass](#getiids)                         | Obtiene una matriz que puede contener la interfaz implementadas por la actual de identificadores `RuntimeClass` objeto. |
| [Getruntimeclassname](#getruntimeclassname) | Obtiene el nombre de clase en tiempo de ejecución del elemento actual `RuntimeClass` objeto.                                  |
| [Gettrustlevel](#gettrustlevel)             | Obtiene el nivel de confianza del actual `RuntimeClass` objeto.                                         |
| [Getweakreference](#getweakreference)       | Obtiene un puntero al objeto de referencia débil actual `RuntimeClass` objeto.                 |
| [Internaladdref](#internaladdref)           | Incrementa el recuento de referencias a la actual `RuntimeClass` objeto.                               |
| [Runtimeclass](#queryinterface)           | Recupera un puntero al identificador de interfaz especificado.                                                 |
| [Runtimeclass](#release)                         | Realiza una operación de liberación de COM en actual `RuntimeClass` objeto.                             |

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

Se trata de un detalle de implementación.

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Espacio de nombres:** Microsoft::WRL

## <a name="tilde-runtimeclass"></a>RuntimeClass:: ~ RuntimeClass

Desinicializa la instancia actual de la `RuntimeClass` clase.

```cpp
virtual ~RuntimeClass();
```

## <a name="addref"></a>Runtimeclass

Incrementa el recuento de referencias actual `RuntimeClass` objeto.

```cpp
STDMETHOD_(
   ULONG,
   AddRef
)();
```

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.

## <a name="decrementreference"></a>Decrementreference

Disminuye el recuento de referencias actual `RuntimeClass` objeto.

```cpp
ULONG DecrementReference();
```

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.

## <a name="getiids"></a>Runtimeclass

Obtiene una matriz que puede contener la interfaz implementadas por la actual de identificadores `RuntimeClass` objeto.

```cpp
STDMETHOD(
   GetIids
)
   (_Out_ ULONG *iidCount,
   _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids);
```

### <a name="parameters"></a>Parámetros

*iidCount*<br/>
Cuando finalice esta operación, el número total de elementos de matriz *IID*.

*IID*<br/>
Cuando se completa esta operación, un puntero a una matriz de identificadores de interfaz.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; en caso contrario, E_OUTOFMEMORY.

## <a name="getruntimeclassname"></a>Getruntimeclassname

Obtiene el nombre de clase en tiempo de ejecución del elemento actual `RuntimeClass` objeto.

```cpp
STDMETHOD( GetRuntimeClassName )(
    _Out_ HSTRING* runtimeName
);
```

### <a name="parameters"></a>Parámetros

*runtimeName*<br/>
Cuando se completa esta operación, el nombre de clase en tiempo de ejecución.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.

### <a name="remarks"></a>Comentarios

Se genera un error de aserción si `__WRL_STRICT__` o `__WRL_FORCE_INSPECTABLE_CLASS_MACRO__` no está definido.

## <a name="gettrustlevel"></a>Gettrustlevel

Obtiene el nivel de confianza del actual `RuntimeClass` objeto.

```cpp
STDMETHOD(GetTrustLevel)(
    _Out_ TrustLevel* trustLvl
);
```

### <a name="parameters"></a>Parámetros

*trustLvl*<br/>
Cuando finalice esta operación, el nivel de confianza del actual `RuntimeClass` objeto.

### <a name="return-value"></a>Valor devuelto

Siempre S_OK.

### <a name="remarks"></a>Comentarios

Se genera un error de aserción si `__WRL_STRICT__` o `__WRL_FORCE_INSPECTABLE_CLASS_MACRO__` no está definido.

## <a name="getweakreference"></a>Getweakreference

Obtiene un puntero al objeto de referencia débil actual `RuntimeClass` objeto.

```cpp
STDMETHOD(
   GetWeakReference
)(_Deref_out_ IWeakReference **weakReference);
```

### <a name="parameters"></a>Parámetros

*weakReference*<br/>
Cuando se completa esta operación, un puntero a un objeto de referencia débil.

### <a name="return-value"></a>Valor devuelto

Siempre S_OK.

## <a name="internaladdref"></a>Internaladdref

Incrementa el recuento de referencias a la actual `RuntimeClass` objeto.

```cpp
ULONG InternalAddRef();
```

### <a name="return-value"></a>Valor devuelto

El recuento de referencias resultante.

## <a name="queryinterface"></a>Runtimeclass

Recupera un puntero al identificador de interfaz especificado.

```cpp
STDMETHOD(
   QueryInterface
)
   (REFIID riid,
   _Deref_out_ void **ppvObject);
```

### <a name="parameters"></a>Parámetros

*riid*<br/>
Id. de interfaz.

*ppvObject*<br/>
Cuando se completa este opereation, un puntero a la interfaz especificada por el *riid* parámetro.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.

## <a name="release"></a>Runtimeclass

Realiza una operación de liberación de COM en actual `RuntimeClass` objeto.

```cpp
STDMETHOD_(
   ULONG,
   Release
)();
```

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.

### <a name="remarks"></a>Comentarios

Si el recuento de referencias se convierte en cero, el `RuntimeClass` se elimina el objeto.

## <a name="runtimeclass"></a>Runtimeclass

Inicializa la instancia actual de la `RuntimeClass` clase.

```cpp
RuntimeClass();
```
