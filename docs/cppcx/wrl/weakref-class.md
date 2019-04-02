---
title: WeakRef (Clase)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::WeakRef
- client/Microsoft::WRL::WeakRef::~WeakRef
- client/Microsoft::WRL::WeakRef::As
- client/Microsoft::WRL::WeakRef::AsIID
- client/Microsoft::WRL::WeakRef::CopyTo
- client/Microsoft::WRL::WeakRef::operator&
- client/Microsoft::WRL::WeakRef::WeakRef
helpviewer_keywords:
- Microsoft::WRL::WeakRef class
- Microsoft::WRL::WeakRef::~WeakRef, destructor
- Microsoft::WRL::WeakRef::As method
- Microsoft::WRL::WeakRef::AsIID method
- Microsoft::WRL::WeakRef::CopyTo method
- Microsoft::WRL::WeakRef::operator& operator
- Microsoft::WRL::WeakRef::WeakRef, constructor
ms.assetid: 572be703-c641-496c-8af5-ad6164670ba1
ms.openlocfilehash: 9616fcffac0b92d5ac6d96cfe5f4119f3a3b180f
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58785979"
---
# <a name="weakref-class"></a>WeakRef (Clase)

Representa una *referencia débil* que solo puede usar Windows en tiempo de ejecución, no COM clásico. Una referencia débil representa un objeto que puede ser o no accesible.

## <a name="syntax"></a>Sintaxis

```cpp
class WeakRef : public ComPtr<IWeakReference>;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[WeakRef::WeakRef (constructor)](#weakref)|Inicializa una nueva instancia de la clase `WeakRef`.|
|[WeakRef::~WeakRef (destructor)](#tilde-weakref)|Desinicializa la instancia actual de la `WeakRef` clase.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[WeakRef::As (método)](#as)|Establece el texto especificado `ComPtr` parámetro de puntero para representar la interfaz especificada.|
|[WeakRef::AsIID (método)](#asiid)|Establece el texto especificado `ComPtr` parámetro de puntero para representar el identificador de interfaz especificado.|
|[WeakRef::CopyTo (método)](#copyto)|Asigna un puntero a una interfaz, si está disponible, para la variable de puntero especificada.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[WeakRef::operator& (operador)](#operator-ampersand-operator)|Devuelve un `ComPtrRef` objeto que representa el actual `WeakRef` objeto.|

## <a name="remarks"></a>Comentarios

Un `WeakRef` objeto mantiene un *referencia fuerte*, que está asociado a un objeto y puede ser válido o no es válido. Llame a la `As()` o `AsIID()` método para obtener una referencia segura. Cuando la referencia segura se válida, puede obtener acceso al objeto asociado. Cuando la referencia segura no es válida (`nullptr`), el objeto asociado es inaccesible.

Un `WeakRef` objeto normalmente se utiliza para representar un objeto cuya existencia se controla mediante una aplicación o un subproceso externo. Por ejemplo, crear un `WeakRef` objeto a partir de una referencia a un objeto de archivo. Mientras el archivo esté abierto, la referencia segura será válida. Sin embargo, si el archivo está abierto, la referencia segura no será válida.

Tenga en cuenta que hay un cambio de comportamiento en los métodos [As](#as), [AsIID](#asiid) y [CopyTo](#copyto) en el SDK de Windows 10. Anteriormente, después de llamar a cualquiera de estos métodos, podría comprobar la `WeakRef` para `nullptr` para determinar si se obtuvo correctamente una referencia segura, como se muestra en el código siguiente:

```cpp
WeakRef wr;
strongComptrRef.AsWeak(&wr);

// Now suppose that the object strongComPtrRef points to no longer exists
// and the following code tries to get a strong ref from the weak ref:
ComPtr<ISomeInterface> strongRef;
HRESULT hr = wr.As(&strongRef);

// This check won't work with the Windows 10 SDK version of the library.
// Check the input pointer instead.
if(wr == nullptr)
{
    wprintf(L"Couldn’t get strong ref!");
}
```

El código anterior no funciona al usar el SDK de Windows 10 (o posterior). En su lugar, compruebe el puntero que se pasó para `nullptr`.

```cpp
if (strongRef == nullptr)
{
    wprintf(L"Couldn't get strong ref!");
}
```

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`ComPtr`

`WeakRef`

## <a name="requirements"></a>Requisitos

**Encabezado:** client.h

**Espacio de nombres**: Microsoft::WRL

## <a name="tilde-weakref"></a>WeakRef:: ~ weakref (destructor)

Desinicializa la instancia actual de la `WeakRef` clase.

```cpp
~WeakRef();
```

## <a name="as"></a>Weakref (método)

Establece el texto especificado `ComPtr` parámetro de puntero para representar la interfaz especificada.

```cpp
template<typename U>
HRESULT As(
   _Out_ ComPtr<U>* ptr
);

template<typename U>
HRESULT As(
   _Out_ Details::ComPtrRef<ComPtr<U>> ptr
);
```

### <a name="parameters"></a>Parámetros

*U*<br/>
Id. de interfaz.

*ptr*<br/>
Cuando finalice esta operación, un objeto que representa el parámetro *U*.

### <a name="return-value"></a>Valor devuelto

- S_OK si esta operación se realiza correctamente; en caso contrario, un HRESULT que indica el motivo del error en la operación, y *ptr* está establecido en `nullptr`.

- S_OK si esta operación se realiza correctamente, pero actual `WeakRef` objeto ya se ha liberado. Parámetro *ptr* está establecido en `nullptr`.

- S_OK si esta operación se realiza correctamente, pero actual `WeakRef` objeto no se deriva de parámetro *U*. Parámetro *ptr* está establecido en `nullptr`.

### <a name="remarks"></a>Comentarios

Se genera un error si parámetro *U* es `IWeakReference`, o no se deriva `IInspectable`.

La primera plantilla es el formulario que debe usar en el código. La segunda plantilla es una especialización del asistente interno, que admite características del lenguaje C++, como palabra clave de deducción de tipos [automática](../../cpp/auto-cpp.md) .

A partir del SDK de Windows 10, este método no establece la `WeakRef` instancia a `nullptr` si no se pudo obtener la referencia débil, por lo que debería evitar código de comprobación de errores que comprueba la `WeakRef` para `nullptr`. En su lugar, compruebe *ptr* para `nullptr`.

## <a name="asiid"></a>Asiid (método)

Establece el texto especificado `ComPtr` parámetro de puntero para representar el identificador de interfaz especificado.

```cpp
HRESULT AsIID(
   REFIID riid,
   _Out_ ComPtr<IInspectable>* ptr
);
```

### <a name="parameters"></a>Parámetros

*riid*<br/>
Id. de interfaz.

*ptr*<br/>
Cuando finalice esta operación, un objeto que representa el parámetro *riid*.

### <a name="return-value"></a>Valor devuelto

- S_OK si esta operación se realiza correctamente; en caso contrario, un HRESULT que indica el motivo del error en la operación, y *ptr* está establecido en `nullptr`.

- S_OK si esta operación se realiza correctamente, pero actual `WeakRef` objeto ya se ha liberado. Parámetro *ptr* está establecido en `nullptr`.

- S_OK si esta operación se realiza correctamente, pero actual `WeakRef` objeto no se deriva de parámetro *riid*. Parámetro *ptr* está establecido en `nullptr`. (Para más información, vea la sección Comentarios.)

### <a name="remarks"></a>Comentarios

Se genera un error si parámetro *riid* no se deriva `IInspectable`. Este error sustituye el valor devuelto.

La primera plantilla es el formulario que debe usar en el código. La segunda plantilla (no se muestra aquí, pero se declara en el archivo de encabezado) es una especialización del asistente interno, que admite características del lenguaje C++, como la palabra clave de deducción de tipos [automática](../../cpp/auto-cpp.md) .

A partir del SDK de Windows 10, este método no establece la `WeakRef` instancia a `nullptr` si no se pudo obtener la referencia débil, por lo que debería evitar código de comprobación de errores que comprueba la `WeakRef` para `nullptr`. En su lugar, compruebe *ptr* para `nullptr`.

## <a name="copyto"></a>Weakref (método)

Asigna un puntero a una interfaz, si está disponible, para la variable de puntero especificada.

```cpp
HRESULT CopyTo(
   REFIID riid,
   _Deref_out_ IInspectable** ptr
);

template<typename U>
HRESULT CopyTo(
   _Deref_out_ U** ptr
);

HRESULT CopyTo(
   _Deref_out_ IWeakReference** ptr
);
```

### <a name="parameters"></a>Parámetros

*U*<br/>
Puntero un `IInspectable` interfaz. Se genera un error si *U* no se deriva `IInspectable`.

*riid*<br/>
Id. de interfaz. Se genera un error si *riid* no se deriva `IWeakReference`.

*ptr*<br/>
Un puntero indirecto doble a `IInspectable` o `IWeakReference`.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que describe el error. Para obtener más información, vea **Comentarios**.

### <a name="remarks"></a>Comentarios

Un valor devuelto de S_OK significa que esta operación se realizó correctamente, pero no indica si la referencia débil se resolvió en una referencia segura. Si se devuelve S_OK, pruebe que ese parámetro *p* una fuerte referencia; es decir, el parámetro *p* no es igual a `nullptr`.

A partir del SDK de Windows 10, este método no establece la `WeakRef` instancia a `nullptr` si no se pudo obtener la referencia débil, por lo que debe evitar error al comprobar el código que comprueba la `WeakRef` para `nullptr`. En su lugar, compruebe *ptr* para `nullptr`.

## <a name="operator-ampersand-operator"></a>Weakref:: operator&amp; operador

Devuelve un `ComPtrRef` objeto que representa el actual `WeakRef` objeto.

```cpp
Details::ComPtrRef<WeakRef> operator&() throw()
```

### <a name="return-value"></a>Valor devuelto

Un `ComPtrRef` objeto que representa el actual `WeakRef` objeto.

### <a name="remarks"></a>Comentarios

Se trata de un operador de aplicación auxiliar interna que no está pensado para usarse en el código.

## <a name="weakref"></a>Constructor de Weakref

Inicializa una nueva instancia de la clase `WeakRef`.

```cpp
WeakRef();
WeakRef(
   decltype(__nullptr)
);

WeakRef(
   _In_opt_ IWeakReference* ptr
);

WeakRef(
   const ComPtr<IWeakReference>& ptr
);

WeakRef(
   const WeakRef& ptr
);

WeakRef(
   _Inout_ WeakRef&& ptr
);
```

### <a name="parameters"></a>Parámetros

*ptr*<br/>
Un puntero, referencia o referencia de valor r a un objeto existente que inicializa actual `WeakRef` objeto.

### <a name="remarks"></a>Comentarios

El primer constructor inicializa vacío `WeakRef` objeto. El segundo constructor inicializa un `WeakRef` objeto de un puntero a la `IWeakReference` interfaz. El tercer constructor inicializa un `WeakRef` objeto a partir de una referencia a un `ComPtr<IWeakReference>` objeto. Los constructores cuarto y quinto Inicializa un `WeakRef` objeto desde otro `WeakRef` objeto.
