---
title: uninitialized_object (clase)
ms.date: 03/27/2019
f1_keywords:
- uninitialized_object
- AMPRT/uninitialized_object
- AMPRT/Concurrency::uninitialized_object
helpviewer_keywords:
- uninitialized_object class
ms.assetid: 6ae3c4e8-64a6-4511-a158-03be197b63af
ms.openlocfilehash: ef7ded0bf925d3430b70064c4979b75e08f9cf45
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127704"
---
# <a name="uninitialized_object-class"></a>uninitialized_object (clase)

La excepción que se produce cuando se usa un objeto no inicializado.

## <a name="syntax"></a>Sintaxis

```cpp
class uninitialized_object : public runtime_exception;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[Constructor de uninitialized_object](#uninitialized_object)|Inicializa una nueva instancia de la clase `uninitialized_object`.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`exception`

`runtime_exception`

`uninitialized_object`

## <a name="requirements"></a>Requisitos

**Encabezado:** amprt. h

**Espacio de nombres:** Concurrency

## <a name="uninitialized_object"></a>uninitialized_object

Construye una nueva instancia de la excepción `uninitialized_object`.

### <a name="syntax"></a>Sintaxis

```cpp
explicit uninitialized_object(
    const char * _Message ) throw();

uninitialized_object() throw();
```

### <a name="parameters"></a>Parámetros

*_Message*<br/>
Descripción del error.

### <a name="return-value"></a>Valor devuelto

Objeto de excepción de `uninitialized_object`.

## <a name="see-also"></a>Consulte también

[Espacio de nombres de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)
