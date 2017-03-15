---
title: "ARM Assembler Diagnostic Messages | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 52b38267-6023-4bdc-a0ef-863362f48eec
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# ARM Assembler Diagnostic Messages
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El ensamblador de ARM de Microsoft \(*armasm*\) emite errores y advertencias de diagnósticos cuando se encuentre con ellos.  En este artículo se describe los mensajes más habituales.  
  
## Sintaxis  
  
```  
  
filename(lineno) : [error|warning] Anum: message  
```  
  
## Mensajes de diagnóstico  
  
### Errores  
 A2193: esta instrucción genera un comportamiento impredecible  
 La arquitectura ARM no puede garantizar lo que ocurre cuando se ejecuta esta instrucción.  Para obtener más información acerca de las formas bien definidas de esta instrucción, consulte el [Manual de referencia de arquitectura de ARM](http://go.microsoft.com/fwlink/?LinkId=246464).  
  
```  
  
ADD r0, r8, pc         ; A2193: this instruction generates unpredictable behavior  
  
```  
  
 A2196: instrucciones no se puede codificar en 16 bits  
 No se puede codificar la instrucción máquina especificada como una instrucción de control de posición de 16 bits.  Especificar una instrucción de 32 bits o reorganizar el código para que aparezca la etiqueta de destino en el rango de una instrucción de 16 bits.  
  
 El ensamblador puede intentar codificar una rama de 16 bits y producir este error, incluso aunque puedan codificarse con una rama de 32 bits.  Puede resolver este problema mediante el uso de la `.W` especificador para marcar de forma explícita la rama como de 32 bits.  
  
```  
  
  ADD.N r0, r1, r2      ; A2196: instruction cannot be encoded in 16 bits  
  
  B.W label             ; OK  
  B.N label             ; A2196: instruction cannot be encoded in 16 bits  
  SPACE 10000  
label  
  
```  
  
 A2202: Sintaxis de instrucciones de Pre\-manual que no se permite en la región de control de posición  
 Código de control de posición debe utilizar la sintaxis de lenguaje de ensamblador unificada \(UAL\).  Ya no se acepta la sintaxis antigua  
  
```  
  
ADDEQS r0, r1         ; A2202: Pre-UAL instruction syntax not allowed in THUMB region  
ADDSEQ r0, r1         ; OK  
  
```  
  
 A2513: Rotación debe ser par  
 En el modo de ARM, existe una sintaxis alternativa para especificar constantes.  En lugar de escribir `#<const>`, puede escribir `#<byte>,#<rot>`, que representa el valor constante que se obtiene haciendo girar el valor `<byte>` de `<rot>`.  Cuando utilice esta sintaxis, debe hacer el valor de `<rot>` incluso.  
  
```  
  
MOV r0, #4, #2       ; OK  
MOV r0, #4, #1       ; A2513: Rotation must be even  
  
```  
  
 A2557: Número incorrecto de bytes a escribir de nuevo  
 En la estructura de NEÓN, cargar y almacenar instrucciones \(`VLDn`, `VSTn`\), existe una sintaxis alternativa para especificar la reescritura en el registro de base.  En lugar de colocar un signo de exclamación \(\!\) después de la dirección, puede especificar un valor inmediato que indica el desplazamiento para ser agregado al registro de base.  Si utiliza esta sintaxis, debe especificar el número exacto de bytes que se han cargado o almacenados por la instrucción.  
  
```  
  
VLD1.8 {d0-d3}, [r0]!         ; OK  
VLD1.8 {d0-d3}, [r0], #32     ; OK  
VLD1.8 {d0-d3}, [r0], #100    ; A2557: Incorrect number of bytes to write back  
  
```  
  
### Advertencias  
 A4228: Valor de alineación supera la alineación de área; alineación no garantizada que  
 La alineación que se especifica en un `ALIGN` la directiva es mayor que la alineación de la envolvente `AREA`.  Como resultado, el ensamblador no puede garantizar que la `ALIGN` se respetará la directiva.  
  
 Para solucionar este problema, puede especificar en el `AREA` Directiva un `ALIGN` atributo es igual o mayor que la alineación que desee.  
  
```  
  
AREA |.myarea1|  
ALIGN 8           ; A4228: Alignment value exceeds AREA alignment; alignment not guaranteed  
  
AREA |.myarea2|,ALIGN=3  
ALIGN 8           ; OK  
  
```  
  
 A4508: El uso de esta constante girado es obsoleto  
 En el modo de ARM, existe una sintaxis alternativa para especificar constantes.  En lugar de escribir `#<const>`, puede escribir `#<byte>,#<rot>`, que representa el valor constante que se obtiene haciendo girar el valor `<byte>` de `<rot>`.  En algunos contextos, ARM ha dejado de utilizar el uso de estas constantes girados.  En estos casos, utilice el basic `#<const>` sintaxis en su lugar.  
  
```  
  
ANDS r0, r0, #1                ; OK  
ANDS r0, r0, #4, #2            ; A4508: Use of this rotated constant is deprecated  
  
```  
  
 A4509: Este formato de instrucción condicional es obsoleta  
 Este formato de instrucción condicional ha dejado de utilizar ARM en la arquitectura de ARMv8.  Le recomendamos que cambie el código para utilizar bifurcaciones condicionales.  Para ver qué instrucciones condicionales aún son compatibles, consulte el [Manual de referencia de arquitectura de ARM](http://go.microsoft.com/fwlink/?LinkId=246464).  
  
 Esta advertencia no es emitido cuando el  `- oldit` se utiliza el modificador de línea de comandos.  
  
```  
  
ADDEQ r0, r1, r8              ; A4509: This form of conditional instruction is deprecated  
  
```  
  
## Vea también  
 [ARM Assembler Command\-Line Reference](../../assembler/arm/arm-assembler-command-line-reference.md)   
 [ARM Assembler Directives](../../assembler/arm/arm-assembler-directives.md)