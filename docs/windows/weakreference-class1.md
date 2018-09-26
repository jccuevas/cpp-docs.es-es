---
title: WeakReference (Class1) | Microsoft Docs
ms.custom: ''
ms.date: 09/24/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::WeakReference
- implements/Microsoft::WRL::Details::WeakReference::DecrementStrongReference
- implements/Microsoft::WRL::Details::WeakReference::IncrementStrongReference
- implements/Microsoft::WRL::Details::WeakReference::Resolve
- implements/Microsoft::WRL::Details::WeakReference::SetUnknown
- implements/Microsoft::WRL::Details::WeakReference::~WeakReference
- implements/Microsoft::WRL::Details::WeakReference::WeakReference
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Details::WeakReference class
- Microsoft::WRL::Details::WeakReference::DecrementStrongReference method
- Microsoft::WRL::Details::WeakReference::IncrementStrongReference method
- Microsoft::WRL::Details::WeakReference::Resolve method
- Microsoft::WRL::Details::WeakReference::SetUnknown method
- Microsoft::WRL::Details::WeakReference::~WeakReference, destructor
- Microsoft::WRL::Details::WeakReference::WeakReference, constructor
ms.assetid: 3f4c956b-dbbd-49b1-8cfa-9509a9956c97
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4d82dbffee5b686c6d8923f395c74fedfac54816
ms.sourcegitcommit: edb46b0239a0e616af4ec58906e12338c3e8d2c6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/25/2018
ms.locfileid: "47169676"
---
# <a name="weakreference-class1"></a>WeakReference (Class1)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
class WeakReference;
```

## <a name="remarks"></a>Comentarios

Representa un *referencia débil* que puede utilizarse con el tiempo de ejecución de Windows o COM clásico. Una referencia débil representa un objeto que puede ser o no accesible.

Un `WeakReference` objeto mantiene un *referencia fuerte*, que es un puntero a un objeto y un *recuento de referencia segura*, que es el número de copias de la referencia segura que se han distribuido por el `Resolve()` método. Aunque el recuento de referencia segura es distinto de cero, la referencia segura no es válida y el objeto es accesible. Cuando el recuento de referencia segura se convierte en cero, la referencia segura no es válida y el objeto no es accesible.

Un `WeakReference` objeto normalmente se utiliza para representar un objeto cuya existencia se controla mediante una aplicación o un subproceso externo. Por ejemplo, crear un `WeakReference` objeto a partir de una referencia a un objeto de archivo. Mientras el archivo esté abierto, la referencia segura será válida. Sin embargo, si el archivo está abierto, la referencia segura no será válida.

El `WeakReference` métodos son seguros para subprocesos.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

Name                                                  | Descripción
----------------------------------------------------- | ---------------------------------------------------------------------------
[WeakReference:: WeakReference](#weakreference)        | Inicializa una nueva instancia de la clase `WeakReference`.
[WeakReference:: ~ WeakReference](#tilde-weakreference) | Desinicializa (destrucción) la instancia actual de la `WeakReference` clase.

### <a name="public-methods"></a>Métodos públicos

Name                                                                 | Descripción
-------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------
[Decrementstrongreference](#decrementstrongreference) | Disminuye el recuento de la referencia segura del actual `WeakReference` objeto.
[Incrementstrongreference](#incrementstrongreference) | Incrementa el recuento de referencia segura del actual `WeakReference` objeto.
[WeakReference:: Resolve](#resolve)                                   | Establece el puntero especificado en el valor de referencia segura actual si el recuento de referencia segura es distinto de cero.
[Setunknown](#setunknown)                             | Establece la referencia segura del actual `WeakReference` objeto en el puntero de interfaz especificado.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`WeakReference`

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Namespace:** wrl

## <a name="tilde-weakreference"></a>WeakReference:: ~ WeakReference

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
virtual ~WeakReference();
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

Desinicializa la instancia actual de la `WeakReference` clase.

## <a name="decrementstrongreference"></a>Decrementstrongreference

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
ULONG DecrementStrongReference();
```

### <a name="remarks"></a>Comentarios

Disminuye el recuento de la referencia segura del actual `WeakReference` objeto.

Cuando el recuento de referencia segura se convierte en cero, la referencia segura se establece en `nullptr`.

### <a name="return-value"></a>Valor devuelto

El recuento de referencia segura disminuye.

## <a name="incrementstrongreference"></a>Incrementstrongreference

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
ULONG IncrementStrongReference();
```

### <a name="return-value"></a>Valor devuelto

El recuento de referencia segura incrementado.

### <a name="remarks"></a>Comentarios

Incrementa el recuento de referencia segura del actual `WeakReference` objeto.

## <a name="resolve"></a>WeakReference:: Resolve

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

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
Cuando se completa esta operación, una copia de la referencia segura actual si el recuento de referencia segura es distinto de cero.

### <a name="return-value"></a>Valor devuelto

- S_OK si esta operación se realiza correctamente y el recuento de referencia segura es cero. El *ppvObject* parámetro está establecido en `nullptr`.

- S_OK si esta operación se realiza correctamente y el recuento de referencia segura es distinto de cero. El *ppvObject* parámetro está establecido en la referencia segura.

- En caso contrario, un HRESULT que indica el motivo por el error de la operación.

### <a name="remarks"></a>Comentarios

Establece el puntero especificado en el valor de referencia segura actual si el recuento de referencia segura es distinto de cero.

## <a name="setunknown"></a>Setunknown

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
void SetUnknown(
   _In_ IUnknown* unk
);
```

### <a name="parameters"></a>Parámetros

*UNK*<br/>
Un puntero a la `IUnknown` interfaz de un objeto.

### <a name="remarks"></a>Comentarios

Establece la referencia segura del actual `WeakReference` objeto en el puntero de interfaz especificado.

## <a name="weakreference"></a>WeakReference:: WeakReference

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
WeakReference();
```

### <a name="remarks"></a>Comentarios

Inicializa una nueva instancia de la clase `WeakReference`.

El puntero de referencia segura para la `WeakReference` objeto se inicializa en `nullptr`, y el recuento de referencia segura se inicializa en 1.
