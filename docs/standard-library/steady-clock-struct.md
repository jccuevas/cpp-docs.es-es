---
title: steady_clock (Struct) | Microsoft Docs
ms.custom: ''
ms.date: 05/22/2018
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
ms.openlocfilehash: 53f4deb0bfe9439011f75cd22d0d52b74dae9c1f
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38959730"
---
# <a name="steadyclock-struct"></a>Struct steady_clock

Representa un *constante* reloj.

## <a name="syntax"></a>Sintaxis

```cpp
struct steady_clock;
```

## <a name="remarks"></a>Comentarios

En Windows, `steady_clock` ajusta el `QueryPerformanceCounter` función.

Un reloj es *monotónico* si el valor devuelto por la primera llamada a `now` siempre es menor o igual que el valor devuelto por una llamada posterior a `now`. Un reloj es *constante* si es *monotónico* y si el tiempo entre los ciclos de reloj es constante.

`high_resolution_clock` es un typedef para `steady_clock`.

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|nombre|Descripción|
|----------|-----------------|
|`steady_clock::duration`|Un sinónimo de `nanoseconds`, definido en \<chrono >.|
|`steady_clock::period`|Un sinónimo de `nano`, definido en \<proporción >.|
|`steady_clock::rep`|Un sinónimo de **largo** **largo**, el tipo que se usa para representar el número de ciclos de reloj en la creación de instancias contenida de `duration`.|
|`steady_clock::time_point`|Sinónimo de `chrono::time_point<steady_clock>`.|

## <a name="public-functions"></a>Funciones públicas

|Función|Descripción|
|--------------|-----------------|
|`now`|Devuelve la hora actual como un `time_point` valor.|

## <a name="public-constants"></a>Constantes públicas

|nombre|Descripción|
|----------|-----------------|
|`steady_clock::is_steady`|Contiene **true**. `steady_clock` es *constante*.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<chrono >

**Espacio de nombres:** std::chrono

## <a name="see-also"></a>Vea también

- [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)
- [\<chrono>](../standard-library/chrono.md)
- [system_clock (Estructura)](../standard-library/system-clock-structure.md)
