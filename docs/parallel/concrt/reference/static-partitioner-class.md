---
title: static_partitioner (clase)
ms.date: 11/04/2016
f1_keywords:
- static_partitioner
- PPL/concurrency::static_partitioner
- PPL/concurrency::static_partitioner::static_partitioner
helpviewer_keywords:
- static_partitioner class
ms.assetid: 2b3dbdf0-6eb9-49f6-8639-03df1d974143
ms.openlocfilehash: 7a58daa27bc7a2f51f78a3068a2f152979ffdd72
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142680"
---
# <a name="static_partitioner-class"></a>static_partitioner (clase)

La clase `static_partitioner` representa una partición estática del intervalo sobre el que se itera mediante `parallel_for`. El particionador divide el intervalo en tantos fragmentos como hay trabajadores disponibles para el programador subyacente.

## <a name="syntax"></a>Sintaxis

```cpp
class static_partitioner;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[static_partitioner](#ctor)|Construye un objeto `static_partitioner`.|
|[~ static_partitioner destructor](#dtor)|Destruye un objeto `static_partitioner`.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`static_partitioner`

## <a name="requirements"></a>Requisitos

**Encabezado:** PPL. h

**Espacio de nombres:** simultaneidad

## <a name="dtor"></a>~ static_partitioner

Destruye un objeto `static_partitioner`.

```cpp
~static_partitioner();
```

## <a name="ctor"></a>static_partitioner

Construye un objeto `static_partitioner`.

```cpp
static_partitioner();
```

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)
