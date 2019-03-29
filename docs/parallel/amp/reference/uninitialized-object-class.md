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
ms.openlocfilehash: 05c24672531d50fa9bc31587e6c6733fdff21f29
ms.sourcegitcommit: 309dc532f13242854b47759cef846de59bb807f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/28/2019
ms.locfileid: "58565550"
---
# <a name="uninitializedobject-class"></a>uninitialized_object (clase)

La excepción que se produce cuando se usa un objeto no inicializado.

## <a name="syntax"></a>Sintaxis

```
class uninitialized_object : public runtime_exception;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[uninitialized_object (Constructor)](#uninitialized_object)|Inicializa una nueva instancia de la clase `uninitialized_object`.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`exception`

`runtime_exception`

`uninitialized_object`

## <a name="requirements"></a>Requisitos

**Encabezado:** amprt.h

**Espacio de nombres**: simultaneidad

## <a name="uninitializedobject"></a>uninitialized_object

Crea una nueva instancia de la `uninitialized_object` excepción.

### <a name="syntax"></a>Sintaxis

```
explicit uninitialized_object(
    const char * _Message ) throw();

uninitialized_object() throw();
```

### <a name="parameters"></a>Parámetros

*_Message*<br/>
Descripción del error.

### <a name="return-value"></a>Valor devuelto

La `uninitialized_object` objeto de excepción.

## <a name="see-also"></a>Vea también

[Espacio de nombres de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)
