---
title: auto_partitioner (clase)
ms.date: 11/04/2016
f1_keywords:
- auto_partitioner
- PPL/concurrency::auto_partitioner
- PPL/concurrency::auto_partitioner::auto_partitioner
helpviewer_keywords:
- auto_partitioner class
ms.assetid: 7cc08e5d-20b4-47a4-b4b5-c214a78f5a9e
ms.openlocfilehash: 4d1d8f19069412240de8e9d69cdcfb34618f2796
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142862"
---
# <a name="auto_partitioner-class"></a>auto_partitioner (clase)

La clase `auto_partitioner` representa a los métodos predeterminados `parallel_for`, `parallel_for_each` y usa `parallel_transform` para dividir el intervalo sobre el que iteran. Este método de creación de particiones emplea el robo de intervalo para el equilibrio de carga, así como la cancelación por iteración.

## <a name="syntax"></a>Sintaxis

```cpp
class auto_partitioner;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[auto_partitioner](#ctor)|Construye un objeto `auto_partitioner`.|
|[~ auto_partitioner destructor](#dtor)|Destruye un objeto `auto_partitioner`.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`auto_partitioner`

## <a name="requirements"></a>Requisitos

**Encabezado:** PPL. h

**Espacio de nombres:** simultaneidad

## <a name="dtor"></a>~ auto_partitioner

Destruye un objeto `auto_partitioner`.

```cpp
~auto_partitioner();
```

## <a name="ctor"></a>auto_partitioner

Construye un objeto `auto_partitioner`.

```cpp
auto_partitioner();
```

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)
