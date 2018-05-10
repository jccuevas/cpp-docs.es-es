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
ms.openlocfilehash: 1a3250d9a090dcbd5eaa9a3cc0d51df84600ed3e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="ltlimitsgt"></a>&lt;limits&gt;

Define la clase de plantilla `numeric_limits` y dos enumeraciones relativas a las representaciones de punto flotante y el redondeo.

## <a name="syntax"></a>Sintaxis

```cpp
#include <limits>

```

## <a name="remarks"></a>Comentarios

Las especializaciones explícitas de la clase `numeric_limits` describen muchas propiedades de los tipos fundamentales, incluidos los tipos de carácter, entero y punto flotante y los `bool` que están definidos por la implementación en lugar de estar fijados por las reglas del lenguaje C++. Las propiedades que se describen en \<limits> incluyen precisión, representaciones de tamaño mínimo y máximo, redondeo y errores de tipo de señalización.

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
