---
title: ActivationFactory (clase) | Microsoft Docs
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c2e8256b90b243bc02f9ca5bbfb8ee6a933a7fe4
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2018
ms.locfileid: "48788648"
---
# <a name="activationfactory-class"></a>ActivationFactory (clase)

Habilita una o más clases que activa Windows Runtime.

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
La interfaz de cero.

*I1*<br/>
La primera interfaz.

*I2*<br/>
La segunda interfaz.

## <a name="remarks"></a>Comentarios

`ActivationFactory` Proporciona métodos de registro y la funcionalidad básica para el `IActivationFactory` interfaz. `ActivationFactory` También le permite proporcionar una implementación de generador personalizado.

El siguiente fragmento de código simbólicamente ilustra cómo usar ActivationFactory.

[!code-cpp[wrl-microsoft__wrl__activationfactory#1](../windows/codesnippet/CPP/activationfactory-class_1.cpp)]

El siguiente fragmento de código muestra cómo usar el [implementa](../windows/implements-structure.md) estructura para especificar más de tres identificadores de interfaz.

`struct MyFactory : ActivationFactory<Implements<I1, I2, I3>, I4, I5>;`

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

Name                                                       | Descripción
---------------------------------------------------------- | ------------------------------------------
[Activationfactory](#activationfactory) | Inicializa el `ActivationFactory` clase.

### <a name="public-methods"></a>Métodos públicos

Name                                                           | Descripción
-------------------------------------------------------------- | --------------------------------------------------------------------------------------------
[Activationfactory](#addref)                           | Incrementa el recuento de referencias del elemento actual `ActivationFactory` objeto.
[Activationfactory](#getiids)                         | Recupera una matriz de identificadores de interfaz implementada.
[Activationfactory](#getruntimeclassname) | Obtiene el nombre de clase en tiempo de ejecución del objeto que actual `ActivationFactory` crea una instancia.
[Activationfactory](#gettrustlevel)             | Obtiene el nivel de confianza del objeto que actual `ActivationFactory` crea una instancia.
[Activationfactory](#queryinterface)           | Recupera un puntero a la interfaz especificada.
[Activationfactory](#release)                         | Disminuye el recuento de referencias del elemento actual `ActivationFactory` objeto.

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

## <a name="activationfactory"></a>Activationfactory

Inicializa el `ActivationFactory` clase.

```cpp
ActivationFactory();
```

## <a name="addref"></a>Activationfactory

Incrementa el recuento de referencias del elemento actual `ActivationFactory` objeto.

```cpp
STDMETHOD_(
   ULONG,
   AddRef
)();
```

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que describe el error.

## <a name="getiids"></a>Activationfactory

Recupera una matriz de identificadores de interfaz implementada.

```cpp
STDMETHOD(
   GetIids
)(_Out_ ULONG *iidCount, _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids);
```

### <a name="parameters"></a>Parámetros

*iidCount*<br/>
Cuando finalice esta operación, el número de identificadores de interfaz en el *IID* matriz.

*IID*<br/>
Cuando se complete esta operación, una matriz de implementa los identificadores de interfaz.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que describe el error. E_OUTOFMEMORY es un valor HRESULT de error posibles.

## <a name="getruntimeclassname"></a>Activationfactory

Obtiene el nombre de clase en tiempo de ejecución del objeto que actual `ActivationFactory` crea una instancia.

```cpp
STDMETHOD(
   GetRuntimeClassName
)(_Out_ HSTRING* runtimeName);
```

### <a name="parameters"></a>Parámetros

*runtimeName*<br/>
Cuando finalice esta operación, un identificador de cadena que contiene el nombre de clase en tiempo de ejecución del objeto que actual `ActivationFactory` crea una instancia.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que describe el error.

## <a name="gettrustlevel"></a>Activationfactory

Obtiene el nivel de confianza del objeto que actual `ActivationFactory` crea una instancia.

```cpp
STDMETHOD(
   GetTrustLevel
)(_Out_ TrustLevel* trustLvl);
```

### <a name="parameters"></a>Parámetros

*trustLvl*<br/>
Cuando se complete esta operación, el nivel de confianza de tiempo de ejecución de la clase que la `ActivationFactory` crea una instancia.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; en caso contrario, se genera un error de aserción y *trustLvl* está establecido en `FullTrust`.

## <a name="queryinterface"></a>Activationfactory

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
Cuando complete esta operación, un puntero a la interfaz especificada por el parámetro *riid*.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que describe el error.

## <a name="release"></a>Activationfactory

Disminuye el recuento de referencias del elemento actual `ActivationFactory` objeto.

```cpp
STDMETHOD_(
   ULONG,
   Release
)();
```

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que describe el error.
