---
title: Excepciones de hardware | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- exceptions [C++], hardware
- errors [C++], low-level
- errors [C++], hardware
- hardware exceptions [C++]
- low level errors
ms.assetid: 06ac6f01-a8cf-4426-bb12-1688315ae1cd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 50cdb9899582b3e398909e4fcb7ad571025dbcf0
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2018
ms.locfileid: "37941579"
---
# <a name="hardware-exceptions"></a>Excepciones de hardware
La mayoría de las excepciones estándar reconocidas por el sistema operativo son excepciones definidas por hardware. Windows reconoce algunas excepciones de software de bajo nivel, pero normalmente el sistema operativo las administra mejor.  
  
 Windows asigna los errores de hardware de los distintos procesadores a los códigos de excepción de esta sección. En algunos casos, un procesador puede generar solo un subconjunto de estas excepciones. Windows preprocesa la información sobre la excepción y emite el código de excepción correspondiente.  
  
 Las excepciones de hardware reconocidas por Windows se resumen en la tabla siguiente:  
  
|Código de excepción|Causa de la excepción|  
|--------------------|------------------------|  
|STATUS_ACCESS_VIOLATION|Lectura o escritura en una ubicación de memoria inaccesible.|  
|STATUS_BREAKPOINT|Detección de un punto de interrupción definido por hardware; se usa solo en depuradores.|  
|STATUS_DATATYPE_MISALIGNMENT|Lectura o escritura de datos en una dirección que no está bien alineada; por ejemplo, las entidades de 16 bits se deben alinear en límites de 2 bytes. (No aplicable a Intel 80*x*86 procesadores.)|  
|STATUS_FLOAT_DIVIDE_BY_ZERO|División del tipo de punto flotante entre 0,0.|  
|STATUS_FLOAT_OVERFLOW|Superación del exponente positivo máximo del tipo de punto flotante.|  
|STATUS_FLOAT_UNDERFLOW|Superación de la magnitud del exponente negativo menor del tipo de punto flotante.|  
|STATUS_FLOATING_RESEVERED_OPERAND|Uso de un formato de punto flotante reservado (uso no válido de formato).|  
|STATUS_ILLEGAL_INSTRUCTION|Intento de ejecución de un código de instrucción no definido por el procesador.|  
|STATUS_PRIVILEGED_INSTRUCTION|Ejecución de una instrucción no permitida en el modo de equipo actual.|  
|STATUS_INTEGER_DIVIDE_BY_ZERO|División de un tipo entero entre 0.|  
|STATUS_INTEGER_OVERFLOW|Intento de operación que supera el intervalo del entero.|  
|STATUS_SINGLE_STEP|Ejecución de una instrucción en modo paso a paso; solo se usa en depuradores.|  
  
 Depuradores, el sistema operativo u otro código de bajo nivel se ocuparán de administrar muchas de las excepciones que se indican en la tabla anterior. El código no debería administrar errores que no sean de enteros y punto flotante. Por lo tanto, lo normal sería usar el filtro de control de excepciones para omitir las excepciones (que se evalúen como 0). En caso contrario, es posible que los mecanismos de nivel inferior no respondan correctamente. Sin embargo, puede tomar las debidas precauciones contra el posible efecto de estos errores de bajo nivel por [escribir controladores de terminación](../cpp/writing-a-termination-handler.md).  
  
## <a name="see-also"></a>Vea también  
 [Escribir un controlador de excepciones](../cpp/writing-an-exception-handler.md)   
 [Control de excepciones estructurado (C/C++)](../cpp/structured-exception-handling-c-cpp.md)