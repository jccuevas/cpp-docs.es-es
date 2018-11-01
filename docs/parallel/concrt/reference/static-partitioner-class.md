---
title: static_partitioner (Clase)
ms.date: 11/04/2016
f1_keywords:
- static_partitioner
- PPL/concurrency::static_partitioner
- PPL/concurrency::static_partitioner::static_partitioner
helpviewer_keywords:
- static_partitioner class
ms.assetid: 2b3dbdf0-6eb9-49f6-8639-03df1d974143
ms.openlocfilehash: a0d06326b2ecbf3c427ae24b45751f7053778a0b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50500898"
---
# <a name="staticpartitioner-class"></a>static_partitioner (Clase)

La clase `static_partitioner` representa una partición estática del intervalo sobre el que se itera mediante `parallel_for`. La clase Partitioner divide el intervalo en tantos fragmentos como trabajadores hay disponibles para el programador subyacente.

## <a name="syntax"></a>Sintaxis

```
class static_partitioner;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[static_partitioner](#ctor)|Construye un objeto `static_partitioner`.|
|[~ static_partitioner (destructor)](#dtor)|Destruye un objeto `static_partitioner`.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`static_partitioner`

## <a name="requirements"></a>Requisitos

**Encabezado:** ppl.h

**Espacio de nombres:** simultaneidad

##  <a name="dtor"></a> ~ static_partitioner)

Destruye un objeto `static_partitioner`.

```
~static_partitioner();
```

##  <a name="ctor"></a> static_partitioner)

Construye un objeto `static_partitioner`.

```
static_partitioner();
```

## <a name="see-also"></a>Vea también

[concurrency (espacio de nombres)](concurrency-namespace.md)
