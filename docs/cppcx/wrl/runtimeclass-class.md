---
title: RuntimeClass (Clase)
ms.date: 09/11/2018
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
ms.openlocfilehash: 64b4124ba3c60fdcb53fc29c7b791c0f73a49579
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376230"
---
# <a name="runtimeclass-class"></a>RuntimeClass (Clase)

Representa una clase WinRT o COM que hereda las interfaces especificadas y proporciona la compatibilidad de Windows Runtime, COM clásica y referencia débil especificada.

Esta clase proporciona la implementación reutilizable de clases `QueryInterface`WinRT y COM, proporcionando la implementación de , `AddRef`, `Release` etc., administra el recuento de referencias del módulo y tiene soporte para proporcionar el generador de clases para objetos activables.

## <a name="syntax"></a>Sintaxis

```cpp
template <typename ...TInterfaces> class RuntimeClass
template <unsigned int classFlags, typename ...TInterfaces> class RuntimeClass;
```

### <a name="parameters"></a>Parámetros

*classFlags*<br/>
Parámetro opcional. Combinación de uno o varios valores de enumeración [RuntimeClassType.](runtimeclasstype-enumeration.md) La `__WRL_CONFIGURATION_LEGACY__` macro se puede definir para cambiar el valor predeterminado de classFlags para todas las clases en tiempo de ejecución del proyecto. Si se define, las instancias runtimeclass no son ágiles de forma predeterminada. Cuando no está definido, runtimeClass instancias son ágiles de forma predeterminada. Para evitar ambiguedades, `Microsoft::WRL::FtmBase` especifique `TInterfaces` `RuntimeClassType::InhibitFtmBase`siempre el in o . Tenga en cuenta que si se utilizan InhibitFtmBase y FtmBase, el objeto será ágil.

*TInterfaces*<br/>
La lista de interfaces que `IUnknown` `IInspectable` el objeto implementa más allá de , u otras interfaces controladas por [RuntimeClassType](runtimeclasstype-enumeration.md). También puede enumerar otras clases de las `Microsoft::WRL::FtmBase` que se derivarán, en `IMarshal`particular para hacer que el objeto sea ágil y hacer que se implemente .

## <a name="members"></a>Miembros

`RuntimeClassInitialize`<br/>
Función que inicializa el `MakeAndInitialize` objeto si se utiliza la función de plantilla para construir el objeto. Devuelve S_OK si el objeto se inicializó correctamente o un código de error COM si se produjo un error en la inicialización. El código de error COM se `MakeAndInitialize`propaga como el valor devuelto de . Tenga en `RuntimeClassInitialize` cuenta que no `Make` se llama al método si se utiliza la función de plantilla para construir el objeto.

### <a name="public-constructors"></a>Constructores públicos

| Nombre                                               | Descripción                                                     |
| -------------------------------------------------- | --------------------------------------------------------------- |
| [RuntimeClass::RuntimeClass](#runtimeclass)        | Inicializa la instancia actual `RuntimeClass` de la clase.   |
| [RuntimeClass::-RuntimeClass](#tilde-runtimeclass) | Desinicializa la instancia `RuntimeClass` actual de la clase. |

### <a name="public-methods"></a>Métodos públicos

| Nombre                                                      | Descripción                                                                                        |
| --------------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| [RuntimeClass::AddRef](#addref)                           | Incrementa el recuento de `RuntimeClass` referencias para el objeto actual.                              |
| [RuntimeClass::DecrementReference](#decrementreference)   | Disminuye el recuento de referencias `RuntimeClass` para el objeto actual.                              |
| [RuntimeClass::GetIids](#getiids)                         | Obtiene una matriz que puede contener los identificadores `RuntimeClass` de interfaz implementados por el objeto actual. |
| [RuntimeClass::GetRuntimeClassName](#getruntimeclassname) | Obtiene el nombre de clase `RuntimeClass` en tiempo de ejecución del objeto actual.                                  |
| [RuntimeClass::GetTrustLevel](#gettrustlevel)             | Obtiene el nivel de `RuntimeClass` confianza del objeto actual.                                         |
| [RuntimeClass::GetWeakReference](#getweakreference)       | Obtiene un puntero al objeto de `RuntimeClass` referencia débil para el objeto actual.                 |
| [RuntimeClass::InternalAddRef](#internaladdref)           | Incrementa el recuento de `RuntimeClass` referencias al objeto actual.                               |
| [RuntimeClass::QueryInterface](#queryinterface)           | Recupera un puntero al identificador de interfaz especificado.                                                 |
| [RuntimeClass::Release](#release)                         | Realiza una operación de `RuntimeClass` liberación COM en el objeto actual.                             |

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

Se trata de un detalle de implementación.

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Espacio de nombres:** Microsoft::WRL

## <a name="runtimeclassruntimeclass"></a><a name="tilde-runtimeclass"></a>RuntimeClass::-RuntimeClass

Desinicializa la instancia `RuntimeClass` actual de la clase.

```cpp
virtual ~RuntimeClass();
```

## <a name="runtimeclassaddref"></a><a name="addref"></a>RuntimeClass::AddRef

Incrementa el recuento de `RuntimeClass` referencias para el objeto actual.

```cpp
STDMETHOD_(
   ULONG,
   AddRef
)();
```

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.

## <a name="runtimeclassdecrementreference"></a><a name="decrementreference"></a>RuntimeClass::DecrementReference

Disminuye el recuento de referencias `RuntimeClass` para el objeto actual.

```cpp
ULONG DecrementReference();
```

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.

## <a name="runtimeclassgetiids"></a><a name="getiids"></a>RuntimeClass::GetIids

Obtiene una matriz que puede contener los identificadores `RuntimeClass` de interfaz implementados por el objeto actual.

```cpp
STDMETHOD(
   GetIids
)
   (_Out_ ULONG *iidCount,
   _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids);
```

### <a name="parameters"></a>Parámetros

*iidCount*<br/>
Cuando se completa esta operación, el número total de elementos en *los identificadores*de matriz .

*iids*<br/>
Cuando se completa esta operación, un puntero a una matriz de interfaces.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, E_OUTOFMEMORY.

## <a name="runtimeclassgetruntimeclassname"></a><a name="getruntimeclassname"></a>RuntimeClass::GetRuntimeClassName

Obtiene el nombre de clase `RuntimeClass` en tiempo de ejecución del objeto actual.

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

### <a name="remarks"></a>Observaciones

Se emite un error `__WRL_STRICT__` `__WRL_FORCE_INSPECTABLE_CLASS_MACRO__` de aserción si está definido o no.

## <a name="runtimeclassgettrustlevel"></a><a name="gettrustlevel"></a>RuntimeClass::GetTrustLevel

Obtiene el nivel de `RuntimeClass` confianza del objeto actual.

```cpp
STDMETHOD(GetTrustLevel)(
    _Out_ TrustLevel* trustLvl
);
```

### <a name="parameters"></a>Parámetros

*trustLvl*<br/>
Cuando se completa esta operación, `RuntimeClass` el nivel de confianza del objeto actual.

### <a name="return-value"></a>Valor devuelto

Siempre S_OK.

### <a name="remarks"></a>Observaciones

Se emite un error `__WRL_STRICT__` `__WRL_FORCE_INSPECTABLE_CLASS_MACRO__` de aserción si está definido o no.

## <a name="runtimeclassgetweakreference"></a><a name="getweakreference"></a>RuntimeClass::GetWeakReference

Obtiene un puntero al objeto de `RuntimeClass` referencia débil para el objeto actual.

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

## <a name="runtimeclassinternaladdref"></a><a name="internaladdref"></a>RuntimeClass::InternalAddRef

Incrementa el recuento de `RuntimeClass` referencias al objeto actual.

```cpp
ULONG InternalAddRef();
```

### <a name="return-value"></a>Valor devuelto

El recuento de referencias resultante.

## <a name="runtimeclassqueryinterface"></a><a name="queryinterface"></a>RuntimeClass::QueryInterface

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
Cuando se completa esta opereta, un puntero a la interfaz especificada por el parámetro *riid.*

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.

## <a name="runtimeclassrelease"></a><a name="release"></a>RuntimeClass::Release

Realiza una operación de `RuntimeClass` liberación COM en el objeto actual.

```cpp
STDMETHOD_(
   ULONG,
   Release
)();
```

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.

### <a name="remarks"></a>Observaciones

Si el recuento de referencias `RuntimeClass` se convierte en cero, se elimina el objeto.

## <a name="runtimeclassruntimeclass"></a><a name="runtimeclass"></a>RuntimeClass::RuntimeClass

Inicializa la instancia actual `RuntimeClass` de la clase.

```cpp
RuntimeClass();
```
