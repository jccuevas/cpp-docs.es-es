---
title: affinity_partitioner (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- affinity_partitioner
- PPL/concurrency::affinity_partitioner
- PPL/concurrency::affinity_partitioner::affinity_partitioner
dev_langs:
- C++
helpviewer_keywords:
- affinity_partitioner class
ms.assetid: 31bf7bb1-bd01-491c-9760-d9d60edfccad
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9b1254b316a52bd3e61b3cafd81ba2e89ee88b62
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46444650"
---
# <a name="affinitypartitioner-class"></a>affinity_partitioner (Clase)

La clase `affinity_partitioner` es similar a la clase `static_partitioner`, pero mejora la afinidad de caché eligiendo la asignación de subintervalos para subprocesos de trabajo. Esta clase puede mejorar considerablemente el rendimiento cuando un bucle se vuelve a ejecutar sobre el mismo conjunto de datos, y los datos se ajustan al caché. Observe que el mismo objeto `affinity_partitioner` debe utilizarse con iteraciones posteriores de un bucle paralelo que se ejecuta sobre un conjunto de datos determinado, para beneficiarse de la situación de los datos.

## <a name="syntax"></a>Sintaxis

```
class affinity_partitioner;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[affinity_partitioner](#ctor)|Construye un objeto `affinity_partitioner`.|
|[~ affinity_partitioner (destructor)](#dtor)|Destruye un `affinity_partitioner` objeto.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`affinity_partitioner`

## <a name="requirements"></a>Requisitos

**Encabezado:** ppl.h

**Espacio de nombres:** simultaneidad

##  <a name="dtor"></a> ~ affinity_partitioner)

Destruye un `affinity_partitioner` objeto.

```
~affinity_partitioner();
```

##  <a name="ctor"></a> affinity_partitioner)

Construye un objeto `affinity_partitioner`.

```
affinity_partitioner();
```

## <a name="see-also"></a>Vea también

[concurrency (espacio de nombres)](concurrency-namespace.md)
