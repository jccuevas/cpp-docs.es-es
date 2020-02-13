---
title: simple_partitioner (clase)
ms.date: 11/04/2016
f1_keywords:
- simple_partitioner
- PPL/concurrency::simple_partitioner
- PPL/concurrency::simple_partitioner::simple_partitioner
helpviewer_keywords:
- simple_partitioner class
ms.assetid: d7e997af-54d1-43f5-abe0-def72df6edb3
ms.openlocfilehash: 503f36b90c5eb3319f9aa2d56528172ffa95bb11
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142498"
---
# <a name="simple_partitioner-class"></a>simple_partitioner (clase)

La clase `simple_partitioner` representa una partición estática del intervalo sobre el que se itera mediante `parallel_for`. La clase Partitioner divide el intervalo en fragmentos de forma que cada fragmento tiene al menos el número de iteraciones especificadas por el tamaño del fragmento.

## <a name="syntax"></a>Sintaxis

```cpp
class simple_partitioner;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[simple_partitioner](#ctor)|Construye un objeto `simple_partitioner`.|
|[~ simple_partitioner destructor](#dtor)|Destruye un objeto `simple_partitioner`.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`simple_partitioner`

## <a name="requirements"></a>Requisitos

**Encabezado:** PPL. h

**Espacio de nombres:** simultaneidad

## <a name="dtor"></a>~ simple_partitioner

Destruye un objeto `simple_partitioner`.

```cpp
~simple_partitioner();
```

## <a name="ctor"></a>simple_partitioner

Construye un objeto `simple_partitioner`.

```cpp
explicit simple_partitioner(_Size_type _Chunk_size);
```

### <a name="parameters"></a>Parámetros

*_Chunk_size*<br/>
Tamaño mínimo de la partición.

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)
