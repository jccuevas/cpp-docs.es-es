---
title: ComPtrRef (clase)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRef
- client/Microsoft::WRL::Details::ComPtrRef::ComPtrRef
- client/Microsoft::WRL::Details::ComPtrRef::GetAddressOf
- client/Microsoft::WRL::Details::ComPtrRef::operator==
- client/Microsoft::WRL::Details::ComPtrRef::operator!=
- client/Microsoft::WRL::Details::ComPtrRef::operator InterfaceType**
- client/Microsoft::WRL::Details::ComPtrRef::operator*
- client/Microsoft::WRL::Details::ComPtrRef::operator T*
- client/Microsoft::WRL::Details::ComPtrRef::operator void**
- client/Microsoft::WRL::Details::ComPtrRef::ReleaseAndGetAddressOf
helpviewer_keywords:
- Microsoft::WRL::Details::ComPtrRef class
- Microsoft::WRL::Details::ComPtrRef::ComPtrRef, constructor
- Microsoft::WRL::Details::ComPtrRef::GetAddressOf method
- Microsoft::WRL::Details::ComPtrRef::operator== operator
- Microsoft::WRL::Details::ComPtrRef::operator!= operator
- Microsoft::WRL::Details::ComPtrRef::operator InterfaceType** operator
- Microsoft::WRL::Details::ComPtrRef::operator* operator
- Microsoft::WRL::Details::ComPtrRef::operator T* operator
- Microsoft::WRL::Details::ComPtrRef::operator void** operator
- Microsoft::WRL::Details::ComPtrRef::ReleaseAndGetAddressOf method
ms.assetid: d6bdfd20-e977-45b4-9ac1-1b8efbdb77de
ms.openlocfilehash: 281e02d85e70a84530e6980d31669a73091448d5
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "58785789"
---
# <a name="comptrref-class"></a>ComPtrRef (clase)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
template <typename T>
class ComPtrRef : public ComPtrRefBase<T>;
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Un [ComPtr\<T >](comptr-class.md) tipo o un tipo derivado de éste, no simplemente la interfaz representada por el `ComPtr`.

## <a name="remarks"></a>Comentarios

Representa una referencia a un objeto de tipo `ComPtr<T>`.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

Name                               | Descripción
---------------------------------- | -------------------------------------------------------------------------------------------------------------
[ComPtrRef::ComPtrRef](#comptrref) | Inicializa una nueva instancia de la `ComPtrRef` clase desde el puntero especificado a otro `ComPtrRef` objeto.

### <a name="public-methods"></a>Métodos públicos

Name                                                         | Descripción
------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------
[ComPtrRef::GetAddressOf](#getaddressof)                     | Recupera la dirección de un puntero a la interfaz representada por el actual `ComPtrRef` objeto.
[ComPtrRef::ReleaseAndGetAddressOf](#releaseandgetaddressof) | Elimina la actual `ComPtrRef` de objetos y devuelve un puntero a una de puntero a la interfaz que se ha representado por la `ComPtrRef` objeto.

### <a name="public-operators"></a>Operadores públicos

Name                                                                     | Descripción
------------------------------------------------------------------------ | -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[Comptrref:: operator InterfaceType **](#operator-interfacetype-star-star) | Elimina la actual `ComPtrRef` de objetos y devuelve un puntero a una de puntero a la interfaz que se ha representado por la `ComPtrRef` objeto.
[Comptrref:: operator T *](#operator-t-star)                               | Devuelve el valor de la [ptr_](comptrrefbase-class.md#ptr) miembro de datos del objeto ComPtrRef actual.
[ComPtrRef::operator void**](#operator-void-star-star)                   | Elimina la actual `ComPtrRef` de objetos, convierte el puntero a la interfaz que se ha representado por la `ComPtrRef` objeto como un puntero-a-puntero-to `void`y, a continuación, devuelve el puntero de conversión.
[ComPtrRef::operator*](#operator-star)                                   | Recupera el puntero a la interfaz representada por el actual `ComPtrRef` objeto.
[ComPtrRef::operator==](#operator-equality)                              | Indica si dos objetos `ComPtrRef` son iguales.
[ComPtrRef::operator!=](#operator-inequality)                            | Indica si dos objetos `ComPtrRef` no son iguales.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`ComPtrRefBase`

`ComPtrRef`

## <a name="requirements"></a>Requisitos

**Encabezado:** client.h

**Espacio de nombres**: Microsoft::WRL::Details

## <a name="comptrref"></a>ComPtrRef::ComPtrRef

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
ComPtrRef(
   _In_opt_ T* ptr
);
```

### <a name="parameters"></a>Parámetros

*ptr*<br/>
El valor subyacente de otro `ComPtrRef` objeto.

### <a name="remarks"></a>Comentarios

Inicializa una nueva instancia de la `ComPtrRef` clase desde el puntero especificado a otro `ComPtrRef` objeto.

## <a name="getaddressof"></a>ComPtrRef::GetAddressOf

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
InterfaceType* const * GetAddressOf() const;
```

### <a name="return-value"></a>Valor devuelto

Dirección de un puntero a la interfaz representada por el actual `ComPtrRef` objeto.

### <a name="remarks"></a>Comentarios

Recupera la dirección de un puntero a la interfaz representada por el actual `ComPtrRef` objeto.

## <a name="operator-equality"></a>ComPtrRef::operator==

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
bool operator==(
   const Details::ComPtrRef<ComPtr<T>>& a,
   const Details::ComPtrRef<ComPtr<U>>& b
);

bool operator==(
   const Details::ComPtrRef<ComPtr<T>>& a,
   decltype(__nullptr)
);

bool operator==(
   decltype(__nullptr),
   const Details::ComPtrRef<ComPtr<T>>& a
);

bool operator==(
   const Details::ComPtrRef<ComPtr<T>>& a,
   void* b
);

bool operator==(
   void* b,
   const Details::ComPtrRef<ComPtr<T>>& a
);
```

### <a name="parameters"></a>Parámetros

*a*<br/>
Referencia a un objeto `ComPtrRef`.

*b*<br/>
Una referencia a otro `ComPtrRef` objeto o un puntero a un tipo anónimo (`void*`).

### <a name="return-value"></a>Valor devuelto

El primer rendimientos de operador **true** si objeto *un* es igual al objeto *b*; en caso contrario, **false**.

Los operadores de la segundo y terceros yield **true** si objeto *un* es igual a **nullptr**; en caso contrario, **false**.

El cuarto y quinto operadores producen **true** si objeto *un* es igual al objeto *b*; en caso contrario, **false**.

### <a name="remarks"></a>Comentarios

Indica si dos objetos `ComPtrRef` son iguales.

## <a name="operator-inequality"></a>ComPtrRef::operator!=

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
bool operator!=(
   const Details::ComPtrRef<ComPtr<T>>& a,
   const Details::ComPtrRef<ComPtr<U>>& b
);

bool operator!=(
   const Details::ComPtrRef<ComPtr<T>>& a,
   decltype(__nullptr)
);

bool operator!=(
   decltype(__nullptr),
   const Details::ComPtrRef<ComPtr<T>>& a
);

bool operator!=(
   const Details::ComPtrRef<ComPtr<T>>& a,
   void* b
);

bool operator!=(
   void* b,
   const Details::ComPtrRef<ComPtr<T>>& a
);
```

### <a name="parameters"></a>Parámetros

*a*<br/>
Referencia a un objeto `ComPtrRef`.

*b*<br/>
Una referencia a otro `ComPtrRef` objeto o un puntero a un objeto anónimo (`void*`).

### <a name="return-value"></a>Valor devuelto

El primer rendimientos de operador **true** si objeto *un* no es igual al objeto *b*; en caso contrario, **false**.

Los operadores de la segundo y terceros yield **true** si objeto *un* no es igual a **nullptr**; en caso contrario, **false**.

El cuarto y quinto operadores producen **true** si objeto *un* no es igual al objeto *b*; en caso contrario, **false**.

### <a name="remarks"></a>Comentarios

Indica si dos objetos `ComPtrRef` no son iguales.

## <a name="operator-interfacetype-star-star"></a>Comptrref:: operator InterfaceType **

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
operator InterfaceType**();
```

### <a name="remarks"></a>Comentarios

Elimina la actual `ComPtrRef` de objetos y devuelve un puntero a una de puntero a la interfaz que se ha representado por la `ComPtrRef` objeto.

## <a name="operator-star"></a>ComPtrRef::operator*

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
InterfaceType* operator *();
```

### <a name="return-value"></a>Valor devuelto

Puntero a la interfaz representada por el actual `ComPtrRef` objeto.

### <a name="remarks"></a>Comentarios

Recupera el puntero a la interfaz representada por el actual `ComPtrRef` objeto.

## <a name="operator-t-star"></a>Comptrref:: operator T *

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
operator T*();
```

### <a name="remarks"></a>Comentarios

Devuelve el valor de la [ptr_](comptrrefbase-class.md#ptr) miembro de datos del elemento actual `ComPtrRef` objeto.

## <a name="operator-void-star-star"></a>Comptrref:: operator void\*\*

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
operator void**() const;
```

### <a name="remarks"></a>Comentarios

Elimina la actual `ComPtrRef` de objetos, convierte el puntero a la interfaz que se ha representado por la `ComPtrRef` objeto como un puntero-a-puntero-to `void`y, a continuación, devuelve el puntero de conversión.

## <a name="releaseandgetaddressof"></a>ComPtrRef::ReleaseAndGetAddressOf

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
InterfaceType** ReleaseAndGetAddressOf();
```

### <a name="return-value"></a>Valor devuelto

Puntero a la interfaz que se ha representado por los eliminados `ComPtrRef` objeto.

### <a name="remarks"></a>Comentarios

Elimina la actual `ComPtrRef` de objetos y devuelve un puntero a una de puntero a la interfaz que se ha representado por la `ComPtrRef` objeto.
