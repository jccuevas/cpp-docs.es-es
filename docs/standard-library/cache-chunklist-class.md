---
title: cache_chunklist (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- allocators/stdext::cache_chunklist
- allocators/stdext::cache_chunklist::allocate
- allocators/stdext::cache_chunklist::deallocate
dev_langs:
- C++
helpviewer_keywords:
- stdext::cache_chunklist
- stdext::cache_chunklist [C++], allocate
- stdext::cache_chunklist [C++], deallocate
ms.assetid: af19eccc-4ae7-4a34-bbb2-81e397424cb9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a71b6a45dbdb882cc666c72296938f970bba52ac
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33844951"
---
# <a name="cachechunklist-class"></a>cache_chunklist (Clase)

Define un [asignador de bloques](../standard-library/allocators-header.md) que asigna y desasigna bloques de memoria de un tamaño único.

## <a name="syntax"></a>Sintaxis

```cpp
template <std::size_t Sz, std::size_t Nelts = 20>
class cache_chunklist
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|`Sz`|El número de elementos de la matriz que se van a asignar.|

## <a name="remarks"></a>Comentarios

Esta clase de plantilla usa `operator new` para asignar fragmentos de memoria binaria, subasignando bloques para asignar almacenamiento para un bloque de memoria cuando sea necesario; almacena bloques de memoria desasignados en una lista libre independiente para cada fragmento y usa `operator delete` para desasignar un fragmento cuando ninguno de los bloques de memoria está en uso.

Cada bloque de memoria contiene `Sz` bytes de memoria utilizable y un puntero al fragmento al que pertenece. Cada fragmento contiene `Nelts` bloques de memoria, tres punteros, un int y los datos que requieren `operator new` y `operator delete`.

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[cache_chunklist](#cache_chunklist)|Construye un objeto de tipo `cache_chunklist`.|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|Descripción|
|-|-|
|[allocate](#allocate)|Asigna un bloque de memoria.|
|[deallocate](#deallocate)|Libera un número especificado de objetos del almacenamiento, a partir de la posición especificada.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<allocators>

**Espacio de nombres:** stdext

## <a name="allocate"></a>  cache_chunklist::allocate

Asigna un bloque de memoria.

```cpp
void *allocate(std::size_t count);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|`count`|El número de elementos de la matriz que se van a asignar.|

### <a name="return-value"></a>Valor devuelto

Un puntero al objeto asignado.

### <a name="remarks"></a>Comentarios

## <a name="cache_chunklist"></a>  cache_chunklist::cache_chunklist

Construye un objeto de tipo `cache_chunklist`.

```cpp
cache_chunklist();
```

### <a name="remarks"></a>Comentarios

## <a name="deallocate"></a>  cache_chunklist::deallocate

Libera un número especificado de objetos del almacenamiento, a partir de la posición especificada.

```cpp
void deallocate(void* ptr, std::size_t count);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|`ptr`|Un puntero al primer objeto que se va a desasignar del almacenamiento.|
|`count`|El número de objetos que se van a desasignar del almacenamiento.|

### <a name="remarks"></a>Comentarios

## <a name="see-also"></a>Vea también

[\<allocators>](../standard-library/allocators-header.md)<br/>
