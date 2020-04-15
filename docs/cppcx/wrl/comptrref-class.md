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
ms.openlocfilehash: df9ded817227547493c04035e0abc3d948e24495
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372632"
---
# <a name="comptrref-class"></a>ComPtrRef (clase)

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
template <typename T>
class ComPtrRef : public ComPtrRefBase<T>;
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Un [ComPtr\<T>](comptr-class.md) tipo o un tipo derivado de él, no simplemente la interfaz representada por el `ComPtr`archivo .

## <a name="remarks"></a>Observaciones

Representa una referencia a un `ComPtr<T>`objeto de tipo .

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

Nombre                               | Descripción
---------------------------------- | -------------------------------------------------------------------------------------------------------------
[Comptrref::Comptrref](#comptrref) | Inicializa una nueva instancia `ComPtrRef` de la clase desde `ComPtrRef` el puntero especificado a otro objeto.

### <a name="public-methods"></a>Métodos públicos

Nombre                                                         | Descripción
------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------
[ComPtrRef::GetAddressOf](#getaddressof)                     | Recupera la dirección de un puntero a la `ComPtrRef` interfaz representada por el objeto actual.
[ComptrRef::ReleaseAndGetAddressOf](#releaseandgetaddressof) | Elimina el `ComPtrRef` objeto actual y devuelve un puntero a un puntero a `ComPtrRef` la interfaz representada por el objeto.

### <a name="public-operators"></a>Operadores públicos

Nombre                                                                     | Descripción
------------------------------------------------------------------------ | -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[ComPtrRef::operator InterfaceType**](#operator-interfacetype-star-star) | Elimina el `ComPtrRef` objeto actual y devuelve un puntero a un puntero a `ComPtrRef` la interfaz representada por el objeto.
[ComPtrRef::operador T*](#operator-t-star)                               | Devuelve el valor del [ptr_](comptrrefbase-class.md#ptr) miembro de datos del objeto ComPtrRef actual.
[ComPtrRef::operador void**](#operator-void-star-star)                   | Elimina el `ComPtrRef` objeto actual, convierte el puntero a la `ComPtrRef` interfaz representada por el objeto `void`como un puntero a puntero a y, a continuación, devuelve el puntero de conversión.
[ComPtrRef::operador*](#operator-star)                                   | Recupera el puntero a la interfaz `ComPtrRef` representada por el objeto actual.
[ComPtrRef::operador](#operator-equality)                              | Indica si dos objetos `ComPtrRef` son iguales.
[ComPtrRef::operador!-](#operator-inequality)                            | Indica si dos objetos `ComPtrRef` no son iguales.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`ComPtrRefBase`

`ComPtrRef`

## <a name="requirements"></a>Requisitos

**Encabezado:** client.h

**Espacio de nombres:** Microsoft::WRL::Details

## <a name="comptrrefcomptrref"></a><a name="comptrref"></a>Comptrref::Comptrref

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

```cpp
ComPtrRef(
   _In_opt_ T* ptr
);
```

### <a name="parameters"></a>Parámetros

*Ptr*<br/>
El valor subyacente `ComPtrRef` de otro objeto.

### <a name="remarks"></a>Observaciones

Inicializa una nueva instancia `ComPtrRef` de la clase desde `ComPtrRef` el puntero especificado a otro objeto.

## <a name="comptrrefgetaddressof"></a><a name="getaddressof"></a>ComPtrRef::GetAddressOf

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

```cpp
InterfaceType* const * GetAddressOf() const;
```

### <a name="return-value"></a>Valor devuelto

Dirección de un puntero a la `ComPtrRef` interfaz representada por el objeto actual.

### <a name="remarks"></a>Observaciones

Recupera la dirección de un puntero a la `ComPtrRef` interfaz representada por el objeto actual.

## <a name="comptrrefoperator"></a><a name="operator-equality"></a>ComPtrRef::operador

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

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

*Un*<br/>
Referencia a un objeto `ComPtrRef`.

*B*<br/>
Una referencia `ComPtrRef` a otro objeto o un`void*`puntero a un tipo anónimo ( ).

### <a name="return-value"></a>Valor devuelto

El primer operador produce **true** si el objeto *a* es igual al objeto *b*; de lo contrario, **false**.

El segundo y tercer operadores producen **true** si el objeto *a* es igual a **nullptr**; de lo contrario, **false**.

Los operadores cuarto y quinto producen **true** si el objeto *a* es igual al objeto *b*; de lo contrario, **false**.

### <a name="remarks"></a>Observaciones

Indica si dos objetos `ComPtrRef` son iguales.

## <a name="comptrrefoperator"></a><a name="operator-inequality"></a>ComPtrRef::operador!-

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

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

*Un*<br/>
Referencia a un objeto `ComPtrRef`.

*B*<br/>
Una referencia `ComPtrRef` a otro objeto o un`void*`puntero a un objeto anónimo ( ).

### <a name="return-value"></a>Valor devuelto

El primer operador produce **true** si el objeto *a* no es igual al objeto *b*; de lo contrario, **false**.

El segundo y tercer operadores producen **true** si el objeto *a* no es igual a **nullptr**; de lo contrario, **false**.

Los operadores cuarto y quinto producen **true** si el objeto *a* no es igual al objeto *b*; de lo contrario, **false**.

### <a name="remarks"></a>Observaciones

Indica si dos objetos `ComPtrRef` no son iguales.

## <a name="comptrrefoperator-interfacetype"></a><a name="operator-interfacetype-star-star"></a>ComPtrRef::operator InterfaceType**

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

```cpp
operator InterfaceType**();
```

### <a name="remarks"></a>Observaciones

Elimina el `ComPtrRef` objeto actual y devuelve un puntero a un puntero a `ComPtrRef` la interfaz representada por el objeto.

## <a name="comptrrefoperator"></a><a name="operator-star"></a>ComPtrRef::operador*

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

```cpp
InterfaceType* operator *();
```

### <a name="return-value"></a>Valor devuelto

Puntero a la interfaz `ComPtrRef` representada por el objeto actual.

### <a name="remarks"></a>Observaciones

Recupera el puntero a la interfaz `ComPtrRef` representada por el objeto actual.

## <a name="comptrrefoperator-t"></a><a name="operator-t-star"></a>ComPtrRef::operador T*

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

```cpp
operator T*();
```

### <a name="remarks"></a>Observaciones

Devuelve el valor del [ptr_](comptrrefbase-class.md#ptr) miembro `ComPtrRef` de datos del objeto actual.

## <a name="comptrrefoperator-void"></a><a name="operator-void-star-star"></a>ComPtrRef::operator void\*\*

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

```cpp
operator void**() const;
```

### <a name="remarks"></a>Observaciones

Elimina el `ComPtrRef` objeto actual, convierte el puntero a la `ComPtrRef` interfaz representada por el objeto `void`como un puntero a puntero a y, a continuación, devuelve el puntero de conversión.

## <a name="comptrrefreleaseandgetaddressof"></a><a name="releaseandgetaddressof"></a>ComptrRef::ReleaseAndGetAddressOf

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

```cpp
InterfaceType** ReleaseAndGetAddressOf();
```

### <a name="return-value"></a>Valor devuelto

Puntero a la interfaz representada `ComPtrRef` por el objeto eliminado.

### <a name="remarks"></a>Observaciones

Elimina el `ComPtrRef` objeto actual y devuelve un puntero a un puntero a `ComPtrRef` la interfaz representada por el objeto.
