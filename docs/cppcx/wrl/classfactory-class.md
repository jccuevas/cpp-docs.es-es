---
title: ClassFactory (clase)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ClassFactory
- module/Microsoft::WRL::ClassFactory::AddRef
- module/Microsoft::WRL::ClassFactory::ClassFactory
- module/Microsoft::WRL::ClassFactory::LockServer
- module/Microsoft::WRL::ClassFactory::QueryInterface
- module/Microsoft::WRL::ClassFactory::Release
helpviewer_keywords:
- Microsoft::WRL::ClassFactory class
- Microsoft::WRL::ClassFactory::AddRef method
- Microsoft::WRL::ClassFactory::ClassFactory, constructor
- Microsoft::WRL::ClassFactory::LockServer method
- Microsoft::WRL::ClassFactory::QueryInterface method
- Microsoft::WRL::ClassFactory::Release method
ms.assetid: f13e6bce-722b-4f18-b7cf-3ffa6345c1db
ms.openlocfilehash: 3b738cc8f439e6653162ab99b0a26e87aa8fee36
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372664"
---
# <a name="classfactory-class"></a>ClassFactory (clase)

Implementa la funcionalidad básica de la interfaz `IClassFactory`.

## <a name="syntax"></a>Sintaxis

```cpp
template <
    typename I0 = Details::Nil,
    typename I1 = Details::Nil,
    typename I2 = Details::Nil
>
class ClassFactory :
    public Details::RuntimeClass<
        typename Details::InterfaceListHelper<
            IClassFactory,
            I0,
            I1,
            I2,
            Details::Nil
        >::TypeT,
        RuntimeClassFlags<ClassicCom | InhibitWeakReference>,
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

Utilícelo `ClassFactory` para proporcionar una implementación de fábrica definida por el usuario.

El siguiente patrón de programación muestra cómo utilizar la estructura [Implements](implements-structure.md) para especificar más de tres interfaces en un generador de clases.

`struct MyFactory : ClassFactory<Implements<I1, I2, I3>, I4, I5>`

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

Nombre                                        | Descripción
------------------------------------------- | -----------
[ClassFactory::ClassFactory](#classfactory) |

### <a name="public-methods"></a>Métodos públicos

Nombre                                            | Descripción
----------------------------------------------- | ----------------------------------------------------------------------------------------------------------------
[ClassFactory::AddRef](#addref)                 | Incrementa el recuento de `ClassFactory` referencias para el objeto actual.
[ClassFactory::LockServer](#lockserver)         | Incrementa o disminuye el número de objetos subyacentes de `ClassFactory` los que realiza el seguimiento el objeto actual.
[ClassFactory::QueryInterface](#queryinterface) | Recupera un puntero a la interfaz especificada por el parámetro.
[ClassFactory::Liberación](#release)               | Disminuye el recuento de referencias `ClassFactory` para el objeto actual.

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

## <a name="requirements"></a>Requisitos

**Encabezado:** module.h

**Espacio de nombres:** Microsoft::WRL

## <a name="classfactoryaddref"></a><a name="addref"></a>ClassFactory::AddRef

Incrementa el recuento de `ClassFactory` referencias para el objeto actual.

```cpp
STDMETHOD_(
   ULONG,
   AddRef
)();
```

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que describe el error.

## <a name="classfactoryclassfactory"></a><a name="classfactory"></a>ClassFactory::ClassFactory

```cpp
WRL_NOTHROW ClassFactory();
```

## <a name="classfactorylockserver"></a><a name="lockserver"></a>ClassFactory::LockServer

Incrementa o disminuye el número de objetos subyacentes de `ClassFactory` los que realiza el seguimiento el objeto actual.

```cpp
STDMETHOD(
   LockServer
)(BOOL fLock);
```

### <a name="parameters"></a>Parámetros

*Rebaño*<br/>
**true** para incrementar el número de objetos de seguimiento. **falso** para disminuir el número de objetos rastreados.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, E_FAIL.

### <a name="remarks"></a>Observaciones

`ClassFactory`realiza un seguimiento de los objetos en una instancia subyacente de la [Module](module-class.md) clase.

## <a name="classfactoryqueryinterface"></a><a name="queryinterface"></a>ClassFactory::QueryInterface

Recupera un puntero a la interfaz especificada por el parámetro.

```cpp
STDMETHOD(
   QueryInterface
)(REFIID riid, _Deref_out_ void **ppvObject);
```

### <a name="parameters"></a>Parámetros

*riid*<br/>
Id. de interfaz.

*ppvObject*<br/>
Cuando se completa esta operación, un puntero a la interfaz especificada por el parámetro *riid*.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que describe el error.

## <a name="classfactoryrelease"></a><a name="release"></a>ClassFactory::Liberación

Disminuye el recuento de referencias `ClassFactory` para el objeto actual.

```cpp
STDMETHOD_(
   ULONG,
   Release
)();
```

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que describe el error.
