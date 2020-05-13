---
title: WeakReference (Clase)
ms.date: 09/24/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::WeakReference
- implements/Microsoft::WRL::Details::WeakReference::DecrementStrongReference
- implements/Microsoft::WRL::Details::WeakReference::IncrementStrongReference
- implements/Microsoft::WRL::Details::WeakReference::Resolve
- implements/Microsoft::WRL::Details::WeakReference::SetUnknown
- implements/Microsoft::WRL::Details::WeakReference::~WeakReference
- implements/Microsoft::WRL::Details::WeakReference::WeakReference
helpviewer_keywords:
- Microsoft::WRL::Details::WeakReference class
- Microsoft::WRL::Details::WeakReference::DecrementStrongReference method
- Microsoft::WRL::Details::WeakReference::IncrementStrongReference method
- Microsoft::WRL::Details::WeakReference::Resolve method
- Microsoft::WRL::Details::WeakReference::SetUnknown method
- Microsoft::WRL::Details::WeakReference::~WeakReference, destructor
- Microsoft::WRL::Details::WeakReference::WeakReference, constructor
ms.assetid: 3f4c956b-dbbd-49b1-8cfa-9509a9956c97
ms.openlocfilehash: a80c0ec14da2a955a95ac84dd3975212ef20ae04
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374217"
---
# <a name="weakreference-class"></a>WeakReference (Clase)

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
class WeakReference;
```

## <a name="remarks"></a>Observaciones

Representa una *referencia débil* que se puede usar con Windows Runtime o COM clásico. Una referencia débil representa un objeto que puede ser o no accesible.

Un `WeakReference` objeto mantiene una *referencia segura,* que es un puntero a un objeto y un recuento de *referencias seguro,* que es el número de copias de la referencia segura que se han distribuido por el `Resolve()` método. Aunque el recuento de referencias seguro es distinto de cero, la referencia segura es válida y el objeto es accesible. Cuando el recuento de referencias seguro se convierte en cero, la referencia segura no es válida y el objeto es inaccesible.

Normalmente, `WeakReference` un objeto se utiliza para representar un objeto cuya existencia está controlada por un subproceso o aplicación externo. Por ejemplo, `WeakReference` construya un objeto a partir de una referencia a un objeto de archivo. Mientras el archivo esté abierto, la referencia segura será válida. Sin embargo, si el archivo está abierto, la referencia segura no será válida.

Los `WeakReference` métodos son seguros para subprocesos.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

Nombre                                                  | Descripción
----------------------------------------------------- | ---------------------------------------------------------------------------
[WeakReference::WeakReference](#weakreference)        | Inicializa una nueva instancia de la clase `WeakReference`.
[Referencia débil::-Referencia débil](#tilde-weakreference) | Desinicializa (destruye) la instancia `WeakReference` actual de la clase.

### <a name="public-methods"></a>Métodos públicos

Nombre                                                                 | Descripción
-------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------
[WeakReference::DecrementStrongReference](#decrementstrongreference) | Disminuye el recuento de referencias fuerte `WeakReference` del objeto actual.
[WeakReference::IncrementStrongReference](#incrementstrongreference) | Incrementa el recuento de `WeakReference` referencias seguro del objeto actual.
[WeakReference::Resolver](#resolve)                                   | Establece el puntero especificado en el valor de referencia seguro actual si el recuento de referencias seguro es distinto de cero.
[WeakReference::SetUnknown](#setunknown)                             | Establece la referencia segura `WeakReference` del objeto actual en el puntero de interfaz especificado.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`WeakReference`

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Espacio de nombres:** Microsoft::WRL::Details

## <a name="weakreferenceweakreference"></a><a name="tilde-weakreference"></a>Referencia débil::-Referencia débil

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

```cpp
virtual ~WeakReference();
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

Desinicializa la instancia `WeakReference` actual de la clase.

## <a name="weakreferencedecrementstrongreference"></a><a name="decrementstrongreference"></a>WeakReference::DecrementStrongReference

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

```cpp
ULONG DecrementStrongReference();
```

### <a name="remarks"></a>Observaciones

Disminuye el recuento de referencias fuerte `WeakReference` del objeto actual.

Cuando el recuento de referencias fuerte se convierte `nullptr`en cero, la referencia fuerte se establece en .

### <a name="return-value"></a>Valor devuelto

El recuento de referencias fuerte decrementado.

## <a name="weakreferenceincrementstrongreference"></a><a name="incrementstrongreference"></a>WeakReference::IncrementStrongReference

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

```cpp
ULONG IncrementStrongReference();
```

### <a name="return-value"></a>Valor devuelto

El recuento de referencias seguro incrementado.

### <a name="remarks"></a>Observaciones

Incrementa el recuento de `WeakReference` referencias seguro del objeto actual.

## <a name="weakreferenceresolve"></a><a name="resolve"></a>WeakReference::Resolver

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

```cpp
STDMETHOD(Resolve)
   (REFIID riid,
   _Deref_out_opt_ IInspectable **ppvObject
);
```

### <a name="parameters"></a>Parámetros

*riid*<br/>
Id. de interfaz.

*ppvObject*<br/>
Cuando se completa esta operación, una copia de la referencia segura actual si el recuento de referencias seguras es distinto de cero.

### <a name="return-value"></a>Valor devuelto

- S_OK si esta operación se realiza correctamente y el recuento de referencias seguras es cero. El parámetro *ppvObject* `nullptr`se establece en .

- S_OK si esta operación se realiza correctamente y el recuento de referencias seguras es distinto de cero. El parámetro *ppvObject* se establece en la referencia segura.

- De lo contrario, un HRESULT que indica el motivo por el que se produjo un error en esta operación.

### <a name="remarks"></a>Observaciones

Establece el puntero especificado en el valor de referencia seguro actual si el recuento de referencias seguro es distinto de cero.

## <a name="weakreferencesetunknown"></a><a name="setunknown"></a>WeakReference::SetUnknown

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

```cpp
void SetUnknown(
   _In_ IUnknown* unk
);
```

### <a name="parameters"></a>Parámetros

*Unk*<br/>
Un puntero `IUnknown` a la interfaz de un objeto.

### <a name="remarks"></a>Observaciones

Establece la referencia segura `WeakReference` del objeto actual en el puntero de interfaz especificado.

## <a name="weakreferenceweakreference"></a><a name="weakreference"></a>WeakReference::WeakReference

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

```cpp
WeakReference();
```

### <a name="remarks"></a>Observaciones

Inicializa una nueva instancia de la clase `WeakReference`.

El puntero de `WeakReference` referencia seguro para `nullptr`el objeto se inicializa en , y el recuento de referencias seguro se inicializa en 1.
