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
ms.openlocfilehash: 1831a816d0967c2ca53f941128639ea368c1b727
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403105"
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

## <a name="remarks"></a>Comentarios

La clase base debe proporcionar un constructor predeterminado.

En el ejemplo de código siguiente se muestra cómo usar SimpleActivationFactory con el [ActivatableClassWithFactoryEx](activatableclass-macros.md) macro.

`ActivatableClassWithFactoryEx(MyClass, SimpleActivationFactory, MyServerName);`

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[SimpleActivationFactory::ActivateInstance (método)](#activateinstance)|Crea una instancia de la interfaz especificada.|
|[SimpleActivationFactory::GetRuntimeClassName (método)](#getruntimeclassname)|Obtiene el nombre de clase en tiempo de ejecución de una instancia de la clase especificada por el *Base* parámetro de plantilla de clase.|
|[SimpleActivationFactory::GetTrustLevel (método)](#gettrustlevel)|Obtiene el nivel de confianza de una instancia de la clase especificada por el *Base* parámetro de plantilla de clase.|

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

**Espacio de nombres**: Microsoft::WRL

## <a name="activateinstance"></a>Simpleactivationfactory (método)

Crea una instancia de la interfaz especificada.

```cpp
STDMETHOD( ActivateInstance )(
    _Deref_out_ IInspectable **ppvObject
);
```

#### <a name="parameters"></a>Parámetros

*ppvObject*<br/>
Cuando finalice esta operación, puntero a una instancia del objeto especificado por el `Base` parámetro de plantilla de clase.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.

### <a name="remarks"></a>Comentarios

Si `__WRL_STRICT__` está definido, se genera un error de aserción si no se deriva de la clase base especificada en el parámetro de plantilla de clase [RuntimeClass](runtimeclass-class.md), o no está configurado con el WinRt o WinRtClassicComMix [ RuntimeClassType](runtimeclasstype-enumeration.md) valor de enumeración.

## <a name="getruntimeclassname"></a>Simpleactivationfactory (método)

Obtiene el nombre de clase en tiempo de ejecución de una instancia de la clase especificada por el `Base` parámetro de plantilla de clase.

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

### <a name="remarks"></a>Comentarios

Si `__WRL_STRICT__` está definido, se genera un error de aserción si la clase especificada por el `Base` no se deriva de parámetro de plantilla de clase [RuntimeClass](runtimeclass-class.md), o no está configurado con el WinRt o WinRtClassicComMix [RuntimeClassType](runtimeclasstype-enumeration.md) valor de enumeración.

## <a name="gettrustlevel"></a>Simpleactivationfactory (método)

Obtiene el nivel de confianza de una instancia de la clase especificada por el `Base` parámetro de plantilla de clase.

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
