---
title: affinity_partitioner (clase)
ms.date: 11/04/2016
f1_keywords:
- affinity_partitioner
- PPL/concurrency::affinity_partitioner
- PPL/concurrency::affinity_partitioner::affinity_partitioner
helpviewer_keywords:
- affinity_partitioner class
ms.assetid: 31bf7bb1-bd01-491c-9760-d9d60edfccad
ms.openlocfilehash: 0ae6bbee49d1b8873190a7054e55f65b40b31b13
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142877"
---
# <a name="affinity_partitioner-class"></a>affinity_partitioner (clase)

La clase `affinity_partitioner` es similar a la clase `static_partitioner`, pero mejora la afinidad de caché eligiendo la asignación de subintervalos para subprocesos de trabajo. Esta clase puede mejorar considerablemente el rendimiento cuando un bucle se vuelve a ejecutar sobre el mismo conjunto de datos, y los datos se ajustan al caché. Observe que el mismo objeto `affinity_partitioner` debe utilizarse con iteraciones posteriores de un bucle paralelo que se ejecuta sobre un conjunto de datos determinado, para beneficiarse de la situación de los datos.

## <a name="syntax"></a>Sintaxis

```cpp
class affinity_partitioner;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[affinity_partitioner](#ctor)|Construye un objeto `affinity_partitioner`.|
|[~ affinity_partitioner destructor](#dtor)|Destruye un objeto `affinity_partitioner`.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`affinity_partitioner`

## <a name="requirements"></a>Requisitos

**Encabezado:** PPL. h

**Espacio de nombres:** simultaneidad

## <a name="dtor"></a>~ affinity_partitioner

Destruye un objeto `affinity_partitioner`.

```cpp
~affinity_partitioner();
```

## <a name="ctor"></a>affinity_partitioner

Construye un objeto `affinity_partitioner`.

```cpp
affinity_partitioner();
```

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)
