---
title: static_partitioner (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- static_partitioner
- PPL/concurrency::static_partitioner
- PPL/concurrency::static_partitioner::static_partitioner
dev_langs:
- C++
helpviewer_keywords:
- static_partitioner class
ms.assetid: 2b3dbdf0-6eb9-49f6-8639-03df1d974143
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: de1b63cf24fbc84130302fcbae2cb965e8d00597
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46376025"
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
