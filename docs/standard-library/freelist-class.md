---
title: freelist (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- allocators/stdext::freelist
- allocators/stdext::freelist::pop
- allocators/stdext::freelist::push
dev_langs:
- C++
helpviewer_keywords:
- stdext::freelist
- stdext::freelist [C++], pop
- stdext::freelist [C++], push
ms.assetid: 8ad7e35c-4c80-4479-8ede-1a2497b06d71
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ae7e56fd33de888ad31a24ad1e3130acc96daa28
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45702835"
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
|*sz*|El número de elementos de la matriz que se van a asignar.|
|*Max*|La clase máxima que representa el número máximo de elementos que se van a almacenar en la lista libre. La clase máxima puede ser [max_none](../standard-library/max-none-class.md), [max_unbounded](../standard-library/max-unbounded-class.md), [max_fixed_size](../standard-library/max-fixed-size-class.md) o [max_variable_size](../standard-library/max-variable-size-class.md).|

## <a name="remarks"></a>Comentarios

Esta clase de plantilla administra una lista de bloques de memoria de tamaño *Sz* con la longitud máxima de la lista determinada por la clase máxima pasada en *Max*.

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[freelist](#freelist)|Construye un objeto de tipo `freelist`.|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|Descripción|
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

|Parámetro|Descripción|
|---------------|-----------------|
|*ptr*|Un puntero al bloque de memoria que se va a agregar a la lista libre.|

### <a name="return-value"></a>Valor devuelto

**True** si el `full` función de la clase máxima devuelve **false**; en caso contrario, el `push` función devuelve **false**.

### <a name="remarks"></a>Comentarios

Si el `full` función de la clase máxima devuelve **false**, esta función miembro agrega el bloque de memoria que apunta *ptr* al principio de la lista.

## <a name="see-also"></a>Vea también

[\<allocators>](../standard-library/allocators-header.md)<br/>
