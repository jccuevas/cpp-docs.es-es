---
title: SimpleActivationFactory (clase)
ms.date: 09/07/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::SimpleActivationFactory
- module/Microsoft::WRL::SimpleActivationFactory::ActivateInstance
- module/Microsoft::WRL::SimpleActivationFactory::GetRuntimeClassName
- module/Microsoft::WRL::SimpleActivationFactory::GetTrustLevel
helpviewer_keywords:
- Microsoft::WRL::SimpleActivationFactory class
- Microsoft::WRL::SimpleActivationFactory::ActivateInstance method
- Microsoft::WRL::SimpleActivationFactory::GetRuntimeClassName method
- Microsoft::WRL::SimpleActivationFactory::GetTrustLevel method
ms.assetid: aff768e0-0038-4fd7-95d2-ad7d308da41c
ms.openlocfilehash: 39e539c63e91b508f51656114ee8fbd68150991f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370939"
---
# <a name="simpleactivationfactory-class"></a>SimpleActivationFactory (clase)

Proporciona un mecanismo fundamental para crear una clase base de Windows en tiempo de ejecución o COM clásico.

## <a name="syntax"></a>Sintaxis

```cpp
template<typename Base>
class SimpleActivationFactory : public ActivationFactory<>;
```

### <a name="parameters"></a>Parámetros

*Base*<br/>
Una clase base.

## <a name="remarks"></a>Observaciones

La clase base debe proporcionar un constructor predeterminado.

En el ejemplo de código siguiente se muestra cómo utilizar SimpleActivationFactory con el [ActivatableClassWithFactoryEx](activatableclass-macros.md) macro.

`ActivatableClassWithFactoryEx(MyClass, SimpleActivationFactory, MyServerName);`

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[SimpleActivationFactory::ActivateInstance (Método)](#activateinstance)|Crea una instancia de la interfaz especificada.|
|[SimpleActivationFactory::GetRuntimeClassName (Método)](#getruntimeclassname)|Obtiene el nombre de clase en tiempo de ejecución de una instancia de la clase especificada por el parámetro de plantilla de clase *Base.*|
|[SimpleActivationFactory::GetTrustLevel (Método)](#gettrustlevel)|Obtiene el nivel de confianza de una instancia de la clase especificada por el parámetro de plantilla de clase *Base.*|

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

`SimpleActivationFactory`

## <a name="requirements"></a>Requisitos

**Encabezado:** module.h

**Espacio de nombres:** Microsoft::WRL

## <a name="simpleactivationfactoryactivateinstance-method"></a><a name="activateinstance"></a>SimpleActivationFactory::ActivateInstance Método

Crea una instancia de la interfaz especificada.

```cpp
STDMETHOD( ActivateInstance )(
    _Deref_out_ IInspectable **ppvObject
);
```

#### <a name="parameters"></a>Parámetros

*ppvObject*<br/>
Cuando se completa esta operación, puntero a una `Base` instancia del objeto especificado por el parámetro de plantilla de clase.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.

### <a name="remarks"></a>Observaciones

Si `__WRL_STRICT__` se define, se emite un error de aserción si la clase base especificada en el parámetro de plantilla de clase no se deriva de [RuntimeClass](runtimeclass-class.md)o no está configurada con el valor de enumeración WinRt o WinRtClassicComMix [RuntimeClassType](runtimeclasstype-enumeration.md) .

## <a name="simpleactivationfactorygetruntimeclassname-method"></a><a name="getruntimeclassname"></a>SimpleActivationFactory::GetRuntimeClassName Método

Obtiene el nombre de clase en tiempo de `Base` ejecución de una instancia de la clase especificada por el parámetro de plantilla de clase.

```cpp
STDMETHOD( GetRuntimeClassName )(
    _Out_ HSTRING* runtimeName
);
```

#### <a name="parameters"></a>Parámetros

*runtimeName*<br/>
Cuando se completa esta operación, el nombre de clase en tiempo de ejecución.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.

### <a name="remarks"></a>Observaciones

Si `__WRL_STRICT__` se define, se emite un error de `Base` aserción si la clase especificada por el parámetro de plantilla de clase no se deriva de [RuntimeClass](runtimeclass-class.md)o no está configurada con el valor de enumeración WinRt o WinRtClassicComMix [RuntimeClassType](runtimeclasstype-enumeration.md) .

## <a name="simpleactivationfactorygettrustlevel-method"></a><a name="gettrustlevel"></a>SimpleActivationFactory::GetTrustLevel Método

Obtiene el nivel de confianza de una instancia `Base` de la clase especificada por el parámetro de plantilla de clase.

```cpp
STDMETHOD(
   GetTrustLevel
)(_Out_ TrustLevel* trustLvl);
```

#### <a name="parameters"></a>Parámetros

*trustLvl*<br/>
Cuando se completa esta operación, el nivel de confianza del objeto de clase actual.

### <a name="return-value"></a>Valor devuelto

Siempre S_OK.
