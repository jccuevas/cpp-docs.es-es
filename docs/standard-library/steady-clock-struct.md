---
title: steady_clock (Struct) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- chrono/std::chrono::steady_clock
dev_langs:
- C++
ms.assetid: 970d12ec-fc80-4391-a2f7-b57b2aec668d
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ba4ebbe6db12fef05bfabd9970d354a7726fcd7d
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
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
