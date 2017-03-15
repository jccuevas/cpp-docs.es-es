---
title: "Excepciones de hardware | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "errores [C++], hardware"
  - "errores [C++], bajo nivel"
  - "excepciones, hardware"
  - "excepciones de hardware"
  - "errores de bajo nivel"
ms.assetid: 06ac6f01-a8cf-4426-bb12-1688315ae1cd
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Excepciones de hardware
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La mayoría de las excepciones estándar reconocidas por el sistema operativo son excepciones definidas por hardware.  Windows reconoce algunas excepciones de software de bajo nivel, pero normalmente el sistema operativo las administra mejor.  
  
 Windows asigna los errores de hardware de los distintos procesadores a los códigos de excepción de esta sección.  En algunos casos, un procesador puede generar solo un subconjunto de estas excepciones.  Windows preprocesa la información sobre la excepción y emite el código de excepción correspondiente.  
  
 Las excepciones de hardware reconocidas por Windows se resumen en la tabla siguiente:  
  
|Código de excepción|Causa de la excepción|  
|-------------------------|---------------------------|  
|**STATUS\_ACCESS\_VIOLATION**|Lectura o escritura en una ubicación de memoria inaccesible.|  
|**STATUS\_BREAKPOINT**|Detección de un punto de interrupción definido por hardware; se usa solo en depuradores.|  
|**STATUS\_DATATYPE\_MISALIGNMENT**|Lectura o escritura de datos en una dirección que no está bien alineada; por ejemplo, las entidades de 16 bits se deben alinear en límites de 2 bytes. \(No aplicable a procesadores Intel 80*x*86\).|  
|**STATUS\_FLOAT\_DIVIDE\_BY\_ZERO**|División del tipo de punto flotante entre 0,0.|  
|**STATUS\_FLOAT\_OVERFLOW**|Superación del exponente positivo máximo del tipo de punto flotante.|  
|**STATUS\_FLOAT\_UNDERFLOW**|Superación de la magnitud del exponente negativo menor del tipo de punto flotante.|  
|**STATUS\_FLOATING\_RESEVERED\_OPERAND**|Uso de un formato de punto flotante reservado \(uso no válido de formato\).|  
|**STATUS\_ILLEGAL\_INSTRUCTION**|Intento de ejecución de un código de instrucción no definido por el procesador.|  
|**STATUS\_PRIVILEGED\_INSTRUCTION**|Ejecución de una instrucción no permitida en el modo de equipo actual.|  
|**STATUS\_INTEGER\_DIVIDE\_BY\_ZERO**|División de un tipo entero entre 0.|  
|**STATUS\_INTEGER\_OVERFLOW**|Intento de operación que supera el intervalo del entero.|  
|**STATUS\_SINGLE\_STEP**|Ejecución de una instrucción en modo paso a paso; solo se usa en depuradores.|  
  
 Depuradores, el sistema operativo u otro código de bajo nivel se ocuparán de administrar muchas de las excepciones que se indican en la tabla anterior.  El código no debería administrar errores que no sean de enteros y punto flotante.  Por lo tanto, lo normal sería usar el filtro de control de excepciones para omitir las excepciones \(que se evalúen como 0\).  En caso contrario, es posible que los mecanismos de nivel inferior no respondan correctamente.  Sin embargo, se pueden tomar las debidas precauciones contra el posible efecto de estos errores de bajo nivel mediante la [escritura de controladores de terminación](../cpp/writing-a-termination-handler.md).  
  
## Vea también  
 [Escribir un controlador de excepciones](../cpp/writing-an-exception-handler.md)   
 [Control de excepciones estructurado](../cpp/structured-exception-handling-c-cpp.md)