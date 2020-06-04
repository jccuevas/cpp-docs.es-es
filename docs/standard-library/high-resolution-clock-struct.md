---
title: struct high_resolution_clock | Microsoft Docs
ms.custom: ''
ms.date: 05/22/2018
ms.technology: cpp-standard-libraries
ms.topic: reference
f1_keywords:
- chrono/std::chrono::high_resolution_clock
dev_langs:
- C++
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0b00b20e7cea4fa24b37ad33d5536eb9844e6953
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68269127"
---
# <a name="steadyclock-struct"></a>Struct steady_clock

Representa un *high_resolution* reloj.

## <a name="syntax"></a>Sintaxis

```cpp
class high_resolution_clock
```

## <a name="members"></a>Miembros

### <a name="typedefs"></a>Typedefs

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|`duration`|Un sinónimo de `nanoseconds`, definido en \<chrono >.|
|`period`|Un sinónimo de `nano`, definido en \<proporción >.|
|`rep`|Un sinónimo de **largo** **largo**, el tipo que se usa para representar el número de ciclos de reloj en la creación de instancias contenida de `duration`.|
|`time_point`|Sinónimo de `chrono::time_point<high_resolution_clock>`.|

## <a name="functions"></a>Funciones

|||
|-|-|
|`now`|Devuelve la hora actual como un `time_point` valor.|

## <a name="constants"></a>Constantes

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|`is_steady`|Contiene **true**. `high_resolution_clock` es *constante*.|
