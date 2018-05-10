---
title: steady_clock (Struct) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- chrono/std::chrono::steady_clock
dev_langs:
- C++
ms.assetid: 970d12ec-fc80-4391-a2f7-b57b2aec668d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e1dbfac1eb8c67c5306bded6e6fd9ee8dacf54b0
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="steadyclock-struct"></a>Struct steady_clock

Representa un reloj `steady`.

## <a name="syntax"></a>Sintaxis

```cpp
struct steady_clock;
```

## <a name="remarks"></a>Comentarios

En Windows, steady_clock ajusta la función QueryPerformanceCounter.

Un reloj es *monotónico* si el valor devuelto por la primera llamada a `now()` siempre es menor o igual que el valor devuelto por una llamada posterior a `now()`.

Un reloj es *constante* si es *monotónico* y si el tiempo entre los ciclos de reloj es constante.

High_resolution_clock es un elemento typdef para steady_clock.

## <a name="public-functions"></a>Funciones públicas

|Función|Descripción|
|--------------|-----------------|
|now|Devuelve la hora actual como un valor time_point.|

## <a name="public-constants"></a>Constantes públicas

|nombre|Descripción|
|----------|-----------------|
|`system_clock::is_steady`|Contiene `true`. `steady_clock` es *constante*.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<chrono >

**Espacio de nombres:** std::chrono

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<chrono>](../standard-library/chrono.md)<br/>
[system_clock (Estructura)](../standard-library/system-clock-structure.md)<br/>
