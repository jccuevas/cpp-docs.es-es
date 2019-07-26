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
ms.openlocfilehash: 8a504f58f9f64aa8b0d26b17090387c5c2b5de21
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454140"
---
# <a name="freelist-class"></a>freelist (Clase)

Administra una lista de bloques de memoria.

## <a name="syntax"></a>Sintaxis

```cpp
template <std::size_t Sz, class Max>
class freelist : public Max
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*Sz*|El número de elementos de la matriz que se van a asignar.|
|*Max*|La clase máxima que representa el número máximo de elementos que se van a almacenar en la lista libre. La clase máxima puede ser [max_none](../standard-library/max-none-class.md), [max_unbounded](../standard-library/max-unbounded-class.md), [max_fixed_size](../standard-library/max-fixed-size-class.md) o [max_variable_size](../standard-library/max-variable-size-class.md).|

## <a name="remarks"></a>Comentarios

Esta clase de plantilla administra una lista de bloques de memoria de tamaño *SZ* con la longitud máxima de la lista determinada por la clase Max pasada en *Max*.

### <a name="constructors"></a>Constructores

|Constructor|DESCRIPCIÓN|
|-|-|
|[freelist](#freelist)|Construye un objeto de tipo `freelist`.|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|DESCRIPCIÓN|
|-|-|
|[pop](#pop)|Quita el primer bloque de memoria de la lista libre.|
|[push](#push)|Agrega un bloque de memoria a la lista.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<allocators>

**Espacio de nombres:** stdext

## <a name="freelist"></a>  freelist::freelist

Construye un objeto de tipo `freelist`.

```cpp
freelist();
```

### <a name="remarks"></a>Comentarios

## <a name="pop"></a>  freelist::pop

Quita el primer bloque de memoria de la lista libre.

```cpp
void *pop();
```

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero al bloque de memoria que se ha quitado de la lista.

### <a name="remarks"></a>Comentarios

La función miembro devuelve NULL si la lista está vacía. En caso contrario, quita el primer bloque de memoria de la lista.

## <a name="push"></a>  freelist::push

Agrega un bloque de memoria a la lista.

```cpp
bool push(void* ptr);
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*ptr*|Un puntero al bloque de memoria que se va a agregar a la lista libre.|

### <a name="return-value"></a>Valor devuelto

**true** si la `full` función de la clase Max devuelve **false**; de lo contrario `push` , la función devuelve **false**.

### <a name="remarks"></a>Comentarios

Si la `full` función de la clase Max devuelve **false**, esta función miembro agrega el bloque de memoria al que apunta *ptr* al encabezado de la lista.

## <a name="see-also"></a>Vea también

[\<allocators>](../standard-library/allocators-header.md)
