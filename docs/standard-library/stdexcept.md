---
title: '&lt;stdexcept&gt;'
ms.date: 11/04/2016
f1_keywords:
- <stdexcept>
helpviewer_keywords:
- stdexcept header
ms.assetid: 495c10b1-1e60-4514-9f8f-7fda11a2f522
ms.openlocfilehash: 8a8c99f2651d10d4fc2aff413a06256127f32d7d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412506"
---
# <a name="ltstdexceptgt"></a>&lt;stdexcept&gt;

Define varias clases estándar usadas para notificar excepciones. Las clases forman una jerarquía de derivación, todas ellas derivadas de la clase [exception](../standard-library/exception-class.md), e incluyen dos tipos generales de excepciones: errores lógicos y errores en tiempo de ejecución. Los errores lógicos son errores producidos por el programador. Se derivan de la clase base logic_error e incluyen:

- `domain_error`

- `invalid_argument`

- `length_error`

- `out_of_range`

Los errores de tiempo de ejecución se producen debido a errores en las funciones de biblioteca o en el sistema de tiempo de ejecución. Se derivan de la clase base runtime_error e incluyen:

- `overflow_error`

- `range_error`

- `underflow_error`

### <a name="classes"></a>Clases

|Clase|Descripción|
|-|-|
|[domain_error (Clase)](../standard-library/domain-error-class.md)|Clase que actúa como la clase base para todas las excepciones iniciadas para notificar un error de dominio.|
|[invalid_argument (Clase)](../standard-library/invalid-argument-class.md)|Clase que actúa como la clase base para todas las excepciones iniciadas para notificar un argumento inválido.|
|[length_error (Clase)](../standard-library/length-error-class.md)|Clase que actúa como la clase base para todas las excepciones iniciadas para informar de un intento de generar un objeto demasiado largo como para poder especificarlo.|
|[logic_error (Clase)](../standard-library/logic-error-class.md)|Clase que actúa como la clase base para todas las excepciones iniciadas para informar de errores supuestamente detectables antes de que se ejecute el programa, como las infracciones de las condiciones lógicas previas.|
|[out_of_range (Clase)](../standard-library/out-of-range-class.md)|Clase que actúa como la clase base para todas las excepciones iniciadas para informar sobre un argumento que está fuera de su rango válido.|
|[overflow_error (Clase)](../standard-library/overflow-error-class.md)|Clase que actúa como la clase base para todas las excepciones iniciadas para notificar un desbordamiento aritmético.|
|[range_error (Clase)](../standard-library/range-error-class.md)|Clase que actúa como la clase base para todas las excepciones iniciadas para notificar un error de rango.|
|[runtime_error (Clase)](../standard-library/runtime-error-class.md)|Clase que actúa como la clase base para todas las excepciones iniciadas para informar de errores supuestamente detectables únicamente cuando se ejecute el programa.|
|[underflow_error (Clase)](../standard-library/underflow-error-class.md)|Clase que actúa como la clase base para todas las excepciones iniciadas para notificar un subdesbordamiento aritmético.|

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
