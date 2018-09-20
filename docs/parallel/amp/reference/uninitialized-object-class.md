---
title: uninitialized_object (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- uninitialized_object
- AMPRT/uninitialized_object
- AMPRT/Concurrency::uninitialized_object
dev_langs:
- C++
helpviewer_keywords:
- uninitialized_object class
ms.assetid: 6ae3c4e8-64a6-4511-a158-03be197b63af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9fada1f3c4c9372e7a979868f60ac559ecc14a79
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46416258"
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
|[uninitialized_object (Constructor)](#ctor)|Inicializa una nueva instancia de la clase `uninitialized_object`.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`exception`

`runtime_exception`

`uninitialized_object`

## <a name="requirements"></a>Requisitos

**Encabezado:** amprt.h

**Espacio de nombres:** Concurrency
## <a name="uninitialized_object__ctor"></a> unsupported_feature)

Crea una nueva instancia de la excepción unsupported_feature.

### <a name="syntax"></a>Sintaxis

```
explicit unsupported_feature(
    const char * _Message ) throw();

unsupported_feature() throw();
```

### <a name="parameters"></a>Parámetros

*_Cuerpo*<br/>
Descripción del error.

### <a name="return-value"></a>Valor devuelto

Objeto `unsupported_feature`.

## <a name="see-also"></a>Vea también

[Espacio de nombres de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)
