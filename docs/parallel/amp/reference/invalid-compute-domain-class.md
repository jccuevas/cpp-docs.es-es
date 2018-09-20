---
title: invalid_compute_domain (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- invalid_compute_domain
- AMPRT/invalid_compute_domain
- AMPRT/Concurrency::invalid_compute_domain::invalid_compute_domain
dev_langs:
- C++
helpviewer_keywords:
- invalid_compute_domain class
ms.assetid: ac7a7166-8bdb-4db1-8caf-ea129ab5117e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 17d0556a349d66f4c70d730108d9cd843b736dfd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46387034"
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

**Espacio de nombres:** Concurrency

## <a name="ctor"></a> invalid_compute_domain)

Inicializa una nueva instancia de la clase.

## <a name="syntax"></a>Sintaxis

```
explicit invalid_compute_domain(
    const char * _Message ) throw();

invalid_compute_domain() throw();
```

### <a name="parameters"></a>Parámetros

*_Cuerpo*<br/>
Descripción del error.

### <a name="return-value"></a>Valor devuelto

Una instancia de la `invalid_compute_domain` clase

## <a name="see-also"></a>Vea también

[Espacio de nombres de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)
