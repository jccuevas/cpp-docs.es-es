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
ms.openlocfilehash: 9a4c169944d56b693efa681bf7089636477012ea
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54337473"
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

## <a name="remarks"></a>Comentarios

La clase base debe proporcionar un constructor predeterminado.

En el ejemplo de código siguiente se muestra cómo usar `SimpleClassFactory` con el [ActivatableClassWithFactoryEx](activatableclass-macros.md) macro.

`ActivatableClassWithFactoryEx(MyClass, SimpleClassFactory, MyServerName);`

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[SimpleClassFactory::CreateInstance (método)](#createinstance)|Crea una instancia de la interfaz especificada.|

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

**Espacio de nombres**: Microsoft::WRL

## <a name="createinstance"></a>Simpleclassfactory (método)

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
Debe ser `nullptr`; en caso contrario, el valor devuelto es CLASS_E_NOAGGREGATION.

SimpleClassFactory no admite la agregación. Si se admite la agregación y el objeto se crea formaba parte de un agregado, *pUnkOuter* sería un puntero al control `IUnknown` interfaz del agregado.

*riid*<br/>
Identificador del objeto para crear la interfaz.

*ppvObject*<br/>
Cuando finalice esta operación, puntero a una instancia del objeto especificado por el *riid* parámetro.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.

### <a name="remarks"></a>Comentarios

Si `__WRL_STRICT__` está definido, se genera un error de aserción si no se deriva de la clase base especificada en el parámetro de plantilla de clase [RuntimeClass](runtimeclass-class.md), o no está configurado con el ClassicCom o WinRtClassicComMix [ RuntimeClassType](runtimeclasstype-enumeration.md) valor de enumeración.
