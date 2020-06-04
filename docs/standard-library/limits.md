---
title: '&lt;limits&gt;'
ms.date: 11/04/2016
f1_keywords:
- limits/std::<limits>
- <limits>
helpviewer_keywords:
- limits header
ms.assetid: e07d6379-5b00-4a3d-a789-40d41538b59e
ms.openlocfilehash: 3ad740975cfff4f65f9e1c800a709cfaca3367db
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687818"
---
# <a name="ltlimitsgt"></a>&lt;limits&gt;

Define la plantilla de clase `numeric_limits` y dos enumeraciones relativas a las representaciones de punto flotante y el redondeo.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<limits>

**Espacio de nombres:** std

## <a name="remarks"></a>Comentarios

Las especializaciones explícitas de la clase `numeric_limits` describen muchas propiedades de los tipos fundamentales, incluidos los tipos de carácter, entero y punto flotante y **bool** que se definen como implementaciones, en lugar de corregirse C++ por las reglas del módulo. Las propiedades que se describen en \<limits> incluyen precisión, representaciones de tamaño mínimo y máximo, redondeo y errores de tipo de señalización.

## <a name="members"></a>Miembros

### <a name="enumerations"></a>Enumeraciones

|||
|-|-|
|[float_denorm_style](../standard-library/limits-enums.md#float_denorm_style)|La enumeración describe los diversos métodos que puede elegir una implementación para representar un valor de punto flotante no normalizado (un valor demasiado pequeño para representarlo como un valor normalizado):|
|[float_round_style](../standard-library/limits-enums.md#float_round_style)|La enumeración describe los diversos métodos que puede elegir una implementación para redondear un valor de punto flotante a un valor entero.|

### <a name="classes"></a>Clases

|||
|-|-|
|[numeric_limits (Clase)](../standard-library/numeric-limits-class.md)|La plantilla de clase describe las propiedades aritméticas de tipos numéricos integrados.|

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)\
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
