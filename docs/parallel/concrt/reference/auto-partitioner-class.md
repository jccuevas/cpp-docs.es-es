---
title: auto_partitioner (Clase)
ms.date: 11/04/2016
f1_keywords:
- auto_partitioner
- PPL/concurrency::auto_partitioner
- PPL/concurrency::auto_partitioner::auto_partitioner
helpviewer_keywords:
- auto_partitioner class
ms.assetid: 7cc08e5d-20b4-47a4-b4b5-c214a78f5a9e
ms.openlocfilehash: 9e4701c39512613bd7525c2cc0e3d24a57e7689d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50644930"
---
# <a name="autopartitioner-class"></a>auto_partitioner (Clase)

La clase `auto_partitioner` representa a los métodos predeterminados `parallel_for`, `parallel_for_each` y usa `parallel_transform` para dividir el intervalo sobre el que iteran. Este método de particiones emplea la apropiación del intervalo para el equilibrio de carga, así como la cancelación por iterar.

## <a name="syntax"></a>Sintaxis

```
class auto_partitioner;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[auto_partitioner](#ctor)|Construye un objeto `auto_partitioner`.|
|[~ auto_partitioner (destructor)](#dtor)|Destruye un objeto `auto_partitioner`.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`auto_partitioner`

## <a name="requirements"></a>Requisitos

**Encabezado:** ppl.h

**Espacio de nombres:** simultaneidad

##  <a name="dtor"></a> ~ auto_partitioner)

Destruye un objeto `auto_partitioner`.

```
~auto_partitioner();
```

##  <a name="ctor"></a> auto_partitioner)

Construye un objeto `auto_partitioner`.

```
auto_partitioner();
```

## <a name="see-also"></a>Vea también

[concurrency (espacio de nombres)](concurrency-namespace.md)
