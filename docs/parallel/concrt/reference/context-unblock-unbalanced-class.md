---
title: context_unblock_unbalanced (clase)
ms.date: 11/04/2016
f1_keywords:
- context_unblock_unbalanced
- CONCRT/concurrency::context_unblock_unbalanced
- CONCRT/concurrency::context_unblock_unbalanced::context_unblock_unbalanced
helpviewer_keywords:
- context_unblock_unbalanced class
ms.assetid: a76066c8-19dd-44fa-959a-6941ec1b0d2d
ms.openlocfilehash: 261ec96c1a83fbec423e6dbbfe403c4db53a2962
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143096"
---
# <a name="context_unblock_unbalanced-class"></a>context_unblock_unbalanced (clase)

Esta clase describe una excepción que se produce cuando se llama a los métodos `Block` y `Unblock` de un objeto `Context` que no están emparejados correctamente.

## <a name="syntax"></a>Sintaxis

```cpp
class context_unblock_unbalanced : public std::exception;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[context_unblock_unbalanced](#ctor)|Sobrecargado. Construye un objeto `context_unblock_unbalanced`.|

## <a name="remarks"></a>Observaciones

Las llamadas a los métodos `Block` y `Unblock` de un objeto `Context` siempre deben estar emparejadas correctamente. El Runtime de simultaneidad permite que las operaciones se realicen en cualquier orden. Por ejemplo, una llamada a `Block` puede ir seguida de una llamada a `Unblock`, o viceversa. Esta excepción se produciría si, por ejemplo, se realizaran dos llamadas al método `Unblock` en una fila, en un objeto `Context` que no se bloqueó.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`exception`

`context_unblock_unbalanced`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrt. h

**Espacio de nombres:** simultaneidad

## <a name="ctor"></a>context_unblock_unbalanced

Construye un objeto `context_unblock_unbalanced`.

```cpp
explicit _CRTIMP context_unblock_unbalanced(_In_z_ const char* _Message) throw();

context_unblock_unbalanced() throw();
```

### <a name="parameters"></a>Parámetros

*_Message*<br/>
Mensaje descriptivo del error.

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)
