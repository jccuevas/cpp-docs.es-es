---
title: SimpleClassFactory (clase)
ms.date: 09/7/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::SimpleClassFactory
- module/Microsoft::WRL::SimpleClassFactory::CreateInstance
helpviewer_keywords:
- Microsoft::WRL::SimpleClassFactory class
- Microsoft::WRL::SimpleClassFactory::CreateInstance method
ms.assetid: 6edda1b2-4e44-4e14-9364-72f519249962
ms.openlocfilehash: 924b9d2c30f11e6f0444d9c647807f1c86dcc411
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373558"
---
# <a name="simpleclassfactory-class"></a>SimpleClassFactory (clase)

Proporciona un mecanismo fundamental para crear una clase base.

## <a name="syntax"></a>Sintaxis

```cpp
template<typename Base>
class SimpleClassFactory : public ClassFactory<>;
```

### <a name="parameters"></a>Parámetros

*Base*<br/>
Una clase base.

## <a name="remarks"></a>Observaciones

La clase base debe proporcionar un constructor predeterminado.

En el ejemplo de código `SimpleClassFactory` siguiente se muestra cómo utilizar con el [ActivatableClassWithFactoryEx](activatableclass-macros.md) macro.

`ActivatableClassWithFactoryEx(MyClass, SimpleClassFactory, MyServerName);`

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[SimpleClassFactory::CreateInstance (Método)](#createinstance)|Crea una instancia de la interfaz especificada.|

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

`ClassFactory`

`SimpleClassFactory`

## <a name="requirements"></a>Requisitos

**Encabezado:** module.h

**Espacio de nombres:** Microsoft::WRL

## <a name="simpleclassfactorycreateinstance-method"></a><a name="createinstance"></a>SimpleClassFactory::CreateInstance Método

Crea una instancia de la interfaz especificada.

```cpp
STDMETHOD( CreateInstance )(
   _Inout_opt_ IUnknown* pUnkOuter,
   REFIID riid,
   _Deref_out_ void** ppvObject
);
```

#### <a name="parameters"></a>Parámetros

*pUnkOuter*<br/>
Debe `nullptr`ser ; de lo contrario, el valor devuelto es CLASS_E_NOAGGREGATION.

SimpleClassFactory no admite la agregación. Si se admitiera la agregación y el objeto que se crea formaba `IUnknown` parte de un agregado, *pUnkOuter* sería un puntero a la interfaz de control del agregado.

*riid*<br/>
ID de interfaz del objeto que se va a crear.

*ppvObject*<br/>
Cuando se completa esta operación, puntero a una instancia del objeto especificado por el *parámetro riid.*

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.

### <a name="remarks"></a>Observaciones

Si `__WRL_STRICT__` se define, se emite un error de aserción si la clase base especificada en el parámetro de plantilla de clase no se deriva de [RuntimeClass](runtimeclass-class.md)o no está configurada con el valor de enumeración ClassicCom o WinRtClassicComMix [RuntimeClassType](runtimeclasstype-enumeration.md) .
