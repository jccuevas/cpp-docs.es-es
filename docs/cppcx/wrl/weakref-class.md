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
ms.openlocfilehash: 681f5a64c3e2902c66facbd4f0ac3a3663a7e79d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374254"
---
# <a name="weakref-class"></a>WeakRef (Clase)

Representa una *referencia débil* que solo puede usar Windows en tiempo de ejecución, no COM clásico. Una referencia débil representa un objeto que puede ser o no accesible.

## <a name="syntax"></a>Sintaxis

```cpp
class WeakRef : public ComPtr<IWeakReference>;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[WeakRef::WeakRef (Constructor)](#weakref)|Inicializa una nueva instancia de la clase `WeakRef`.|
|[WeakRef::~WeakRef (Destructor)](#tilde-weakref)|Desinicializa la instancia `WeakRef` actual de la clase.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[WeakRef::As (método)](#as)|Establece el `ComPtr` parámetro de puntero especificado para representar la interfaz especificada.|
|[WeakRef::AsIID (método)](#asiid)|Establece el `ComPtr` parámetro de puntero especificado para representar el identificador de interfaz especificado.|
|[WeakRef::CopyTo (método)](#copyto)|Asigna un puntero a una interfaz, si está disponible, para la variable de puntero especificada.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[WeakRef::operator& (operador)](#operator-ampersand-operator)|Devuelve `ComPtrRef` un objeto que `WeakRef` representa el objeto actual.|

## <a name="remarks"></a>Observaciones

Un `WeakRef` objeto mantiene una *referencia segura,* que está asociada a un objeto y puede ser válido o no válido. Llame `As()` al `AsIID()` método o para obtener una referencia segura. Cuando la referencia segura se válida, puede obtener acceso al objeto asociado. Cuando la referencia segura no es válida (`nullptr`), el objeto asociado es inaccesible.

Normalmente, `WeakRef` un objeto se utiliza para representar un objeto cuya existencia está controlada por un subproceso o aplicación externo. Por ejemplo, `WeakRef` construya un objeto a partir de una referencia a un objeto de archivo. Mientras el archivo esté abierto, la referencia segura será válida. Sin embargo, si el archivo está abierto, la referencia segura no será válida.

Tenga en cuenta que hay un cambio de comportamiento en los métodos [As](#as), [AsIID](#asiid) y [CopyTo](#copyto) en el SDK de Windows 10. Anteriormente, después de llamar a `WeakRef` cualquiera `nullptr` de estos métodos, se podía comprobar la opción para determinar si se obtuvo correctamente una referencia segura, como en el código siguiente:

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

El código anterior no funciona al usar el SDK de Windows 10 (o posterior). En su lugar, compruebe el `nullptr`puntero que se pasó en busca de .

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

**Espacio de nombres:** Microsoft::WRL

## <a name="weakrefweakref-destructor"></a><a name="tilde-weakref"></a>WeakRef::-Destructor WeakRef

Desinicializa la instancia `WeakRef` actual de la clase.

```cpp
~WeakRef();
```

## <a name="weakrefas-method"></a><a name="as"></a>WeakRef::As Método

Establece el `ComPtr` parámetro de puntero especificado para representar la interfaz especificada.

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

*Ptr*<br/>
Cuando se completa esta operación, un objeto que representa el parámetro *U*.

### <a name="return-value"></a>Valor devuelto

- S_OK si esta operación se realiza correctamente; de lo contrario, un HRESULT que indica *ptr* el motivo `nullptr`por el que se produjo un error en la operación, y ptr se establece en .

- S_OK si esta operación se `WeakRef` realiza correctamente, pero el objeto actual ya se ha liberado. El *ptr* parámetro ptr `nullptr`se establece en .

- S_OK si esta operación se `WeakRef` realiza correctamente, pero el objeto actual no se deriva del parámetro *U*. El *ptr* parámetro ptr `nullptr`se establece en .

### <a name="remarks"></a>Observaciones

Se emite un error *U* si `IWeakReference`el parámetro U `IInspectable`es , o no se deriva de .

La primera plantilla es el formulario que debe usar en el código. La segunda plantilla es una especialización del asistente interno, que admite características del lenguaje C++, como palabra clave de deducción de tipos [automática](../../cpp/auto-cpp.md) .

A partir del SDK de Windows 10, `WeakRef` `nullptr` este método no establece la instancia en si no se pudo `WeakRef` obtener `nullptr`la referencia débil, por lo que debe evitar comprobar errores el código que comprueba el archivo . En su lugar, compruebe *ptr* para `nullptr`.

## <a name="weakrefasiid-method"></a><a name="asiid"></a>Método WeakRef::AsIID

Establece el `ComPtr` parámetro de puntero especificado para representar el identificador de interfaz especificado.

```cpp
HRESULT AsIID(
   REFIID riid,
   _Out_ ComPtr<IInspectable>* ptr
);
```

### <a name="parameters"></a>Parámetros

*riid*<br/>
Id. de interfaz.

*Ptr*<br/>
Cuando se completa esta operación, un objeto que representa el parámetro *riid*.

### <a name="return-value"></a>Valor devuelto

- S_OK si esta operación se realiza correctamente; de lo contrario, un HRESULT que indica *ptr* el motivo `nullptr`por el que se produjo un error en la operación, y ptr se establece en .

- S_OK si esta operación se `WeakRef` realiza correctamente, pero el objeto actual ya se ha liberado. El *ptr* parámetro ptr `nullptr`se establece en .

- S_OK si esta operación se `WeakRef` realiza correctamente, pero el objeto actual no se deriva del parámetro *riid*. El *ptr* parámetro ptr `nullptr`se establece en . (Para más información, vea la sección Comentarios.)

### <a name="remarks"></a>Observaciones

Se emite un error si el parámetro `IInspectable` *riid* no se deriva de . Este error sustituye el valor devuelto.

La primera plantilla es el formulario que debe usar en el código. La segunda plantilla (no se muestra aquí, pero se declara en el archivo de encabezado) es una especialización del asistente interno, que admite características del lenguaje C++, como la palabra clave de deducción de tipos [automática](../../cpp/auto-cpp.md) .

A partir del SDK de Windows 10, `WeakRef` `nullptr` este método no establece la instancia en si no se pudo `WeakRef` obtener `nullptr`la referencia débil, por lo que debe evitar comprobar errores el código que comprueba el archivo . En su lugar, compruebe *ptr* para `nullptr`.

## <a name="weakrefcopyto-method"></a><a name="copyto"></a>WeakRef::CopyTo Método

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
Puntero `IInspectable` a una interfaz. Se emite un error si *U* `IInspectable`no se deriva de .

*riid*<br/>
Id. de interfaz. Se emite un error si *riid* `IWeakReference`no se deriva de .

*Ptr*<br/>
Un puntero doblemente indirecto a `IInspectable` o `IWeakReference`.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que describe el error. Para obtener más información, consulte **Comentarios**.

### <a name="remarks"></a>Observaciones

Un valor devuelto de S_OK significa que esta operación se realizó correctamente, pero no indica si la referencia débil se resolvió en una referencia segura. Si se devuelve S_OK, pruebe ese parámetro *p* es una referencia segura; es decir, *p* el parámetro p `nullptr`no es igual a .

A partir del SDK de Windows 10, `WeakRef` `nullptr` este método no establece la instancia en si no se pudo `WeakRef` `nullptr`obtener la referencia débil, por lo que debe evitar la comprobación de errores de código que comprueba el archivo . En su lugar, compruebe *ptr* para `nullptr`.

## <a name="weakrefoperatoramp-operator"></a><a name="operator-ampersand-operator"></a>WeakRef::operador&amp; Operador

Devuelve `ComPtrRef` un objeto que `WeakRef` representa el objeto actual.

```cpp
Details::ComPtrRef<WeakRef> operator&() throw()
```

### <a name="return-value"></a>Valor devuelto

Objeto `ComPtrRef` que representa el `WeakRef` objeto actual.

### <a name="remarks"></a>Observaciones

Se trata de un operador auxiliar interno que no está diseñado para usarse en el código.

## <a name="weakrefweakref-constructor"></a><a name="weakref"></a>WeakRef::WeakRef Constructor

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

*Ptr*<br/>
Puntero, referencia o referencia rvalue a un objeto existente `WeakRef` que inicializa el objeto actual.

### <a name="remarks"></a>Observaciones

El primer constructor inicializa `WeakRef` un objeto vacío. El segundo constructor `WeakRef` inicializa un objeto `IWeakReference` desde un puntero a la interfaz. El tercer constructor `WeakRef` inicializa un objeto `ComPtr<IWeakReference>` a partir de una referencia a un objeto. El cuarto y quinto constructores inicializa un `WeakRef` objeto desde otro `WeakRef` objeto.
