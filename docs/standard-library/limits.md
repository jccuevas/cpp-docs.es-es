---
title: '&lt;limits&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- limits/std::<limits>
- <limits>
dev_langs:
- C++
helpviewer_keywords:
- limits header
ms.assetid: e07d6379-5b00-4a3d-a789-40d41538b59e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 66f9401bed0a6c9d0b1ffa09a10f98afa258069d
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38964761"
---
# <a name="ltlimitsgt"></a>&lt;limits&gt;

Define la clase de plantilla `numeric_limits` y dos enumeraciones relativas a las representaciones de punto flotante y el redondeo.

## <a name="syntax"></a>Sintaxis

```cpp
#include <limits>

```

## <a name="remarks"></a>Comentarios

Las especializaciones explícitas de la `numeric_limits` clase describen muchas de las propiedades de los tipos fundamentales, incluido el carácter, entero y tipos de punto flotante y **bool** que son la implementación definida en lugar de corregir las reglas del lenguaje C++. Las propiedades que se describen en \<limits> incluyen precisión, representaciones de tamaño mínimo y máximo, redondeo y errores de tipo de señalización.

### <a name="enumerations"></a>Enumeraciones

|||
|-|-|
|[float_denorm_style](../standard-library/limits-enums.md#float_denorm_style)|La enumeración describe los diversos métodos que puede elegir una implementación para representar un valor de punto flotante no normalizado (un valor demasiado pequeño para representarlo como un valor normalizado):|
|[float_round_style](../standard-library/limits-enums.md#float_round_style)|La enumeración describe los diversos métodos que puede elegir una implementación para redondear un valor de punto flotante a un valor entero.|

### <a name="classes"></a>Clases

|Clase|Descripción|
|-|-|
|[numeric_limits (Clase)](../standard-library/numeric-limits-class.md)|La clase de plantilla describe propiedades aritméticas de tipos numéricos integrados.|

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
