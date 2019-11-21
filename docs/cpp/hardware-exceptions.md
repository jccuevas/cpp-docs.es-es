---
title: Excepciones de hardware
ms.date: 11/04/2016
helpviewer_keywords:
- exceptions [C++], hardware
- errors [C++], low-level
- errors [C++], hardware
- hardware exceptions [C++]
- low level errors
ms.assetid: 06ac6f01-a8cf-4426-bb12-1688315ae1cd
ms.openlocfilehash: 59b74f47cd86d94b50ab9213b3e517c2b08db696
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246551"
---
# <a name="hardware-exceptions"></a>Excepciones de hardware

La mayoría de las excepciones estándar reconocidas por el sistema operativo son excepciones definidas por hardware. Windows reconoce algunas excepciones de software de bajo nivel, pero normalmente el sistema operativo las administra mejor.

Windows asigna los errores de hardware de los distintos procesadores a los códigos de excepción de esta sección. En algunos casos, un procesador puede generar solo un subconjunto de estas excepciones. Windows preprocesa la información sobre la excepción y emite el código de excepción correspondiente.

Las excepciones de hardware reconocidas por Windows se resumen en la tabla siguiente:

|Código de excepción|Causa de la excepción|
|--------------------|------------------------|
|STATUS_ACCESS_VIOLATION|Lectura o escritura en una ubicación de memoria inaccesible.|
|STATUS_BREAKPOINT|Detección de un punto de interrupción definido por hardware; se usa solo en depuradores.|
|STATUS_DATATYPE_MISALIGNMENT|Lectura o escritura de datos en una dirección que no está bien alineada; por ejemplo, las entidades de 16 bits se deben alinear en límites de 2 bytes. (Not applicable to Intel 80*x*86 processors.)|
|STATUS_FLOAT_DIVIDE_BY_ZERO|División del tipo de punto flotante entre 0,0.|
|STATUS_FLOAT_OVERFLOW|Superación del exponente positivo máximo del tipo de punto flotante.|
|STATUS_FLOAT_UNDERFLOW|Superación de la magnitud del exponente negativo menor del tipo de punto flotante.|
|STATUS_FLOATING_RESEVERED_OPERAND|Uso de un formato de punto flotante reservado (uso no válido de formato).|
|STATUS_ILLEGAL_INSTRUCTION|Intento de ejecución de un código de instrucción no definido por el procesador.|
|STATUS_PRIVILEGED_INSTRUCTION|Ejecución de una instrucción no permitida en el modo de equipo actual.|
|STATUS_INTEGER_DIVIDE_BY_ZERO|División de un tipo entero entre 0.|
|STATUS_INTEGER_OVERFLOW|Intento de operación que supera el intervalo del entero.|
|STATUS_SINGLE_STEP|Ejecución de una instrucción en modo paso a paso; solo se usa en depuradores.|

Depuradores, el sistema operativo u otro código de bajo nivel se ocuparán de administrar muchas de las excepciones que se indican en la tabla anterior. El código no debería administrar errores que no sean de enteros y punto flotante. Por lo tanto, lo normal sería usar el filtro de control de excepciones para omitir las excepciones (que se evalúen como 0). En caso contrario, es posible que los mecanismos de nivel inferior no respondan correctamente. You can, however, take appropriate precautions against the potential effect of these low-level errors by [writing termination handlers](../cpp/writing-a-termination-handler.md).

## <a name="see-also"></a>Vea también

[Writing an exception handler](../cpp/writing-an-exception-handler.md)<br/>
[Control de excepciones estructurado (C/C++)](../cpp/structured-exception-handling-c-cpp.md)