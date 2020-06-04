---
title: ActivationFactory (clase)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ActivationFactory
- module/Microsoft::WRL::ActivationFactory::ActivationFactory
- module/Microsoft::WRL::ActivationFactory::AddRef
- module/Microsoft::WRL::ActivationFactory::GetIids
- module/Microsoft::WRL::ActivationFactory::GetRuntimeClassName
- module/Microsoft::WRL::ActivationFactory::GetTrustLevel
- module/Microsoft::WRL::ActivationFactory::QueryInterface
- module/Microsoft::WRL::ActivationFactory::Release
helpviewer_keywords:
- Microsoft::WRL::ActivationFactory class
- Microsoft::WRL::ActivationFactory::ActivationFactory, constructor
- Microsoft::WRL::ActivationFactory::AddRef method
- Microsoft::WRL::ActivationFactory::GetIids method
- Microsoft::WRL::ActivationFactory::GetRuntimeClassName method
- Microsoft::WRL::ActivationFactory::GetTrustLevel method
- Microsoft::WRL::ActivationFactory::QueryInterface method
- Microsoft::WRL::ActivationFactory::Release method
ms.assetid: 5faddf1f-43b6-4f8a-97de-8c9d3ae1e1ff
ms.openlocfilehash: 0655caeb3f49a18e9c57c78f0008901aaaedda4a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368703"
---
# <a name="activationfactory-class"></a>ActivationFactory (clase)

Habilita una o más clases que activa Windows en tiempo de ejecución.

## <a name="syntax"></a>Sintaxis

```cpp
template <
    typename I0 = Details::Nil,
    typename I1 = Details::Nil,
    typename I2 = Details::Nil
>
class ActivationFactory :
    public Details::RuntimeClass<
        typename Details::InterfaceListHelper<
            IActivationFactory,
            I0,
            I1,
            I2,
            Details::Nil
        >::TypeT,
        RuntimeClassFlags<WinRt | InhibitWeakReference>,
        false
    >;
```

### <a name="parameters"></a>Parámetros

*I0*<br/>
La interfaz cero.

*I1*<br/>
La primera interfaz.

*I2*<br/>
La segunda interfaz.

## <a name="remarks"></a>Observaciones

`ActivationFactory`proporciona métodos de registro `IActivationFactory` y funcionalidad básica para la interfaz. `ActivationFactory`también le permite proporcionar una implementación de fábrica personalizada.

El siguiente fragmento de código ilustra simbólicamente cómo utilizar ActivationFactory.

[!code-cpp[wrl-microsoft__wrl__activationfactory#1](../codesnippet/CPP/activationfactory-class_1.cpp)]

El siguiente fragmento de código muestra cómo utilizar la estructura [Implements](implements-structure.md) para especificar más de tres identificadores de interfaz.

`struct MyFactory : ActivationFactory<Implements<I1, I2, I3>, I4, I5>;`

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

Nombre                                                       | Descripción
---------------------------------------------------------- | ------------------------------------------
[ActivationFactory::ActivationFactory](#activationfactory) | Inicializa la clase `ActivationFactory`.

### <a name="public-methods"></a>Métodos públicos

Nombre                                                           | Descripción
-------------------------------------------------------------- | --------------------------------------------------------------------------------------------
[ActivationFactory::AddRef](#addref)                           | Incrementa el recuento de `ActivationFactory` referencias del objeto actual.
[ActivationFactory::GetIids](#getiids)                         | Recupera una matriz de interfaces implementadas.
[ActivationFactory::GetRuntimeClassName](#getruntimeclassname) | Obtiene el nombre de clase en `ActivationFactory` tiempo de ejecución del objeto que crea una instancia del objeto actual.
[ActivationFactory::GetTrustLevel](#gettrustlevel)             | Obtiene el nivel de confianza del `ActivationFactory` objeto que crea una instancia del objeto actual.
[ActivationFactory::QueryInterface](#queryinterface)           | Recupera un puntero a la interfaz especificada.
[ActivationFactory::Release](#release)                         | Disminuye el recuento de referencias `ActivationFactory` del objeto actual.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`I0`

`ChainInterfaces`

`I0`

`RuntimeClassBase`

`ImplementsHelper`

`DontUseNewUseMake`

`RuntimeClassFlags`

`RuntimeClassBaseT`

`RuntimeClass`

`ActivationFactory`

## <a name="requirements"></a>Requisitos

**Encabezado:** module.h

**Espacio de nombres:** Microsoft::WRL

## <a name="activationfactoryactivationfactory"></a><a name="activationfactory"></a>ActivationFactory::ActivationFactory

Inicializa la clase `ActivationFactory`.

```cpp
ActivationFactory();
```

## <a name="activationfactoryaddref"></a><a name="addref"></a>ActivationFactory::AddRef

Incrementa el recuento de `ActivationFactory` referencias del objeto actual.

```cpp
STDMETHOD_(
   ULONG,
   AddRef
)();
```

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que describe el error.

## <a name="activationfactorygetiids"></a><a name="getiids"></a>ActivationFactory::GetIids

Recupera una matriz de interfaces implementadas.

```cpp
STDMETHOD(
   GetIids
)(_Out_ ULONG *iidCount, _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids);
```

### <a name="parameters"></a>Parámetros

*iidCount*<br/>
Cuando se completa esta operación, el número de identificadores de interace en la matriz *iids.*

*iids*<br/>
Cuando se completa esta operación, una matriz de interfaces implementadas.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que describe el error. E_OUTOFMEMORY es un posible error HRESULT.

## <a name="activationfactorygetruntimeclassname"></a><a name="getruntimeclassname"></a>ActivationFactory::GetRuntimeClassName

Obtiene el nombre de clase en `ActivationFactory` tiempo de ejecución del objeto que crea una instancia del objeto actual.

```cpp
STDMETHOD(
   GetRuntimeClassName
)(_Out_ HSTRING* runtimeName);
```

### <a name="parameters"></a>Parámetros

*runtimeName*<br/>
Cuando se completa esta operación, un identificador de una cadena que `ActivationFactory` contiene el nombre de clase en tiempo de ejecución del objeto que crea una instancia actual.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que describe el error.

## <a name="activationfactorygettrustlevel"></a><a name="gettrustlevel"></a>ActivationFactory::GetTrustLevel

Obtiene el nivel de confianza del `ActivationFactory` objeto que crea una instancia del objeto actual.

```cpp
STDMETHOD(
   GetTrustLevel
)(_Out_ TrustLevel* trustLvl);
```

### <a name="parameters"></a>Parámetros

*trustLvl*<br/>
Cuando se completa esta operación, el nivel `ActivationFactory` de confianza de la clase en tiempo de ejecución que crea una instancia.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, se emite un error `FullTrust`de aserción y *trustLvl* se establece en .

## <a name="activationfactoryqueryinterface"></a><a name="queryinterface"></a>ActivationFactory::QueryInterface

Recupera un puntero a la interfaz especificada.

```cpp
STDMETHOD(
   QueryInterface
)(REFIID riid, _Deref_out_ void **ppvObject);
```

### <a name="parameters"></a>Parámetros

*riid*<br/>
Id. de interfaz.

*ppvObject*<br/>
Una vez completada esta operación, un puntero a la interfaz especificada por el parámetro *riid*.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que describe el error.

## <a name="activationfactoryrelease"></a><a name="release"></a>ActivationFactory::Release

Disminuye el recuento de referencias `ActivationFactory` del objeto actual.

```cpp
STDMETHOD_(
   ULONG,
   Release
)();
```

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que describe el error.
