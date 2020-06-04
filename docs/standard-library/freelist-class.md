---
title: freelist (Clase)
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::freelist
- allocators/stdext::freelist::pop
- allocators/stdext::freelist::push
helpviewer_keywords:
- stdext::freelist
- stdext::freelist [C++], pop
- stdext::freelist [C++], push
ms.assetid: 8ad7e35c-4c80-4479-8ede-1a2497b06d71
ms.openlocfilehash: 712c1f1638b954d1580eb527dd9eab7401917517
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317207"
---
# <a name="freelist-class"></a>freelist (Clase)

Administra una lista de bloques de memoria.

## <a name="syntax"></a>Sintaxis

```cpp
template <std::size_t Sz, class Max>
class freelist : public Max
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*Sz*|El número de elementos de la matriz que se van a asignar.|
|*máximo*|La clase máxima que representa el número máximo de elementos que se van a almacenar en la lista libre. La clase máxima puede ser [max_none](../standard-library/max-none-class.md), [max_unbounded](../standard-library/max-unbounded-class.md), [max_fixed_size](../standard-library/max-fixed-size-class.md) o [max_variable_size](../standard-library/max-variable-size-class.md).|

## <a name="remarks"></a>Observaciones

Esta plantilla de clase administra una lista de bloques de memoria de tamaño *Sz* con la longitud máxima de la lista determinada por la clase max pasada en *Max*.

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[freelist](#freelist)|Construye un objeto de tipo `freelist`.|

### <a name="member-functions"></a>Funciones miembro

|Función de miembro|Descripción|
|-|-|
|[Pop](#pop)|Quita el primer bloque de memoria de la lista libre.|
|[push](#push)|Agrega un bloque de memoria a la lista.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<allocators>

**Espacio de nombres:** stdext

## <a name="freelistfreelist"></a><a name="freelist"></a>freelist::freelist

Construye un objeto de tipo `freelist`.

```cpp
freelist();
```

### <a name="remarks"></a>Observaciones

## <a name="freelistpop"></a><a name="pop"></a>freelist::pop

Quita el primer bloque de memoria de la lista libre.

```cpp
void *pop();
```

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero al bloque de memoria que se ha quitado de la lista.

### <a name="remarks"></a>Observaciones

La función miembro devuelve NULL si la lista está vacía. En caso contrario, quita el primer bloque de memoria de la lista.

## <a name="freelistpush"></a><a name="push"></a>freelist::push

Agrega un bloque de memoria a la lista.

```cpp
bool push(void* ptr);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*Ptr*|Un puntero al bloque de memoria que se va a agregar a la lista libre.|

### <a name="return-value"></a>Valor devuelto

**true** si `full` la función de la clase max devuelve **false**; de lo `push` contrario, la función devuelve **false**.

### <a name="remarks"></a>Observaciones

Si `full` la función de la clase max devuelve **false**, esta función miembro agrega el bloque de memoria señalado por *ptr* al jefe de la lista.

## <a name="see-also"></a>Consulte también

[\<asignadores>](../standard-library/allocators-header.md)
