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
ms.openlocfilehash: edf41bbdf92d6e2f00982d9392179b203d00b848
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50645320"
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
La interfaz de cero.

*I1*<br/>
La primera interfaz.

*I2*<br/>
La segunda interfaz.

## <a name="remarks"></a>Comentarios

Utilizar `ClassFactory` para proporcionar una implementación de fábrica definido por el usuario.

El modelo de programación siguiente muestra cómo utilizar el [implementa](../windows/implements-structure.md) estructura para especificar más de tres interfaces en un generador de clases.

`struct MyFactory : ClassFactory<Implements<I1, I2, I3>, I4, I5>`

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

Name                                        | Descripción
------------------------------------------- | -----------
[ClassFactory](#classfactory) |

### <a name="public-methods"></a>Métodos públicos

Name                                            | Descripción
----------------------------------------------- | ----------------------------------------------------------------------------------------------------------------
[ClassFactory](#addref)                 | Incrementa el recuento de referencias actual `ClassFactory` objeto.
[Lockserver](#lockserver)         | Incrementa o disminuye el número de subyacentes de objetos que se realiza el seguimiento actual `ClassFactory` objeto.
[ClassFactory](#queryinterface) | Recupera un puntero a la interfaz especificada por el parámetro.
[ClassFactory](#release)               | Disminuye el recuento de referencias actual `ClassFactory` objeto.

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

## <a name="addref"></a>ClassFactory

Incrementa el recuento de referencias actual `ClassFactory` objeto.

```cpp
STDMETHOD_(
   ULONG,
   AddRef
)();
```

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que describe el error.

## <a name="classfactory"></a>ClassFactory

```cpp
WRL_NOTHROW ClassFactory();
```

## <a name="lockserver"></a>Lockserver

Incrementa o disminuye el número de subyacentes de objetos que se realiza el seguimiento actual `ClassFactory` objeto.

```cpp
STDMETHOD(
   LockServer
)(BOOL fLock);
```

### <a name="parameters"></a>Parámetros

*manada*<br/>
**True** para incrementar el número de objetos con seguimiento. **false** para reducir el número de objetos con seguimiento.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; en caso contrario, E_FAIL.

### <a name="remarks"></a>Comentarios

`ClassFactory` realiza un seguimiento de los objetos en una instancia subyacente de la [módulo](../windows/module-class.md) clase.

## <a name="queryinterface"></a>ClassFactory

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
Cuando finalice esta operación, un puntero a la interfaz especificada por el parámetro *riid*.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que describe el error.

## <a name="release"></a>ClassFactory

Disminuye el recuento de referencias actual `ClassFactory` objeto.

```cpp
STDMETHOD_(
   ULONG,
   Release
)();
```

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que describe el error.
