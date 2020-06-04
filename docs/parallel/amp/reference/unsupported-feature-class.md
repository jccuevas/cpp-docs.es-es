---
title: unsupported_feature (Clase)
ms.date: 03/27/2019
f1_keywords:
- unsupported_feature
- AMPRT/unsupported_feature
- AMPRT/Concurrency::unsupported_feature
helpviewer_keywords:
- unsupported_feature class
ms.assetid: 6b1ab917-df13-48c7-9648-7cb2465a0ff5
ms.openlocfilehash: 561f0a258943f6d7e1c0f1b5cae716592c931fbc
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127717"
---
# <a name="unsupported_feature-class"></a>unsupported_feature (Clase)

La excepción que se produce cuando se usa una función no compatible.

## <a name="syntax"></a>Sintaxis

```cpp
class unsupported_feature : public runtime_exception;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[Constructor de unsupported_feature](#unsupported_feature)|Construye una nueva instancia de la excepción `unsupported_feature`.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`exception`

`runtime_exception`

`unsupported_feature`

## <a name="unsupported_feature"></a>unsupported_feature

  Construye una nueva instancia de la excepción `unsupported_feature`.

### <a name="syntax"></a>Sintaxis

```cpp
explicit unsupported_feature(
    const char * _Message ) throw();

unsupported_feature() throw();
```

### <a name="parameters"></a>Parámetros

*_Message*<br/>
Descripción del error.

### <a name="return-value"></a>Valor devuelto

Objeto `unsupported_feature`.

## <a name="requirements"></a>Requisitos

**Encabezado:** amprt. h

**Espacio de nombres:** Concurrency

## <a name="see-also"></a>Consulte también

[Espacio de nombres de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)
