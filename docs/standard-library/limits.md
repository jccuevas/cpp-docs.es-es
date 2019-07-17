---
title: '&lt;limits&gt;'
ms.date: 11/04/2016
f1_keywords:
- limits/std::<limits>
- <limits>
helpviewer_keywords:
- limits header
ms.assetid: e07d6379-5b00-4a3d-a789-40d41538b59e
ms.openlocfilehash: e23c47b3eaecec92e462af7b2cc47627c5bad86a
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245315"
---
# <a name="ltlimitsgt"></a>&lt;limits&gt;

Define la clase de plantilla `numeric_limits` y dos enumeraciones relativas a las representaciones de punto flotante y el redondeo.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<limits>

**Espacio de nombres:** std

## <a name="remarks"></a>Comentarios

Las especializaciones explícitas de la `numeric_limits` clase describen muchas de las propiedades de los tipos fundamentales, incluido el carácter, entero y tipos de punto flotante y **bool** que son la implementación definida en lugar de corregir las reglas del lenguaje C++. Las propiedades que se describen en \<limits> incluyen precisión, representaciones de tamaño mínimo y máximo, redondeo y errores de tipo de señalización.

## <a name="members"></a>Miembros

### <a name="enumerations"></a>Enumeraciones

|||
|-|-|
|[float_denorm_style](../standard-library/limits-enums.md#float_denorm_style)|La enumeración describe los diversos métodos que puede elegir una implementación para representar un valor de punto flotante no normalizado (un valor demasiado pequeño para representarlo como un valor normalizado):|
|[float_round_style](../standard-library/limits-enums.md#float_round_style)|La enumeración describe los diversos métodos que puede elegir una implementación para redondear un valor de punto flotante a un valor entero.|

### <a name="classes"></a>Clases

|||
|-|-|
|[Clase numeric_limits](../standard-library/numeric-limits-class.md)|La clase de plantilla describe propiedades aritméticas de tipos numéricos integrados.|

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
