---
title: invalid_compute_domain (clase)
ms.date: 11/04/2016
f1_keywords:
- invalid_compute_domain
- AMPRT/invalid_compute_domain
- AMPRT/Concurrency::invalid_compute_domain::invalid_compute_domain
helpviewer_keywords:
- invalid_compute_domain class
ms.assetid: ac7a7166-8bdb-4db1-8caf-ea129ab5117e
ms.openlocfilehash: 51fcd9e42bc4497131da5adb3dff72efb46537b3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62351724"
---
# <a name="invalidcomputedomain-class"></a>invalid_compute_domain (clase)

La excepción que se produce cuando el tiempo de ejecución no puede iniciar un kernel usando el dominio del cálculo especificado en el [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each) sitio de llamada.

## <a name="syntax"></a>Sintaxis

```
class invalid_compute_domain : public runtime_exception;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[invalid_compute_domain Constructor](#ctor)|Inicializa una nueva instancia de la clase `invalid_compute_domain`.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`exception`

`runtime_exception`

`invalid_compute_domain`

## <a name="requirements"></a>Requisitos

**Encabezado:** amprt.h

**Espacio de nombres**: simultaneidad

## <a name="ctor"></a> invalid_compute_domain

Inicializa una nueva instancia de la clase.

## <a name="syntax"></a>Sintaxis

```
explicit invalid_compute_domain(
    const char * _Message ) throw();

invalid_compute_domain() throw();
```

### <a name="parameters"></a>Parámetros

*_Message*<br/>
Descripción del error.

### <a name="return-value"></a>Valor devuelto

Una instancia de la `invalid_compute_domain` clase

## <a name="see-also"></a>Vea también

[Espacio de nombres de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)
