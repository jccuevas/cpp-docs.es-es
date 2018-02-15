---
title: "Mensajes de diagnóstico del ensamblador ARM | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
ms.assetid: 52b38267-6023-4bdc-a0ef-863362f48eec
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 54dca3a864ca34107314ad33725793297fd93e4a
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="arm-assembler-diagnostic-messages"></a>Mensajes de diagnóstico del ensamblador de ARM
El ensamblador de ARM de Microsoft (*armasm*) emite errores y advertencias de diagnóstico cuando encuentra ellos. Este artículo describen los mensajes más habituales.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
filename(lineno) : [error|warning] Anum: message  
```  
  
## <a name="diagnostic-messages"></a>Mensajes de diagnóstico  
  
### <a name="errors"></a>Errores  
 A2193: esta instrucción genera un comportamiento impredecible  
 La arquitectura ARM no puede garantizar qué ocurre cuando se ejecuta esta instrucción.  Para obtener más información acerca de las formas bien definidas de esta instrucción, consulte la [Manual de referencia de arquitectura de ARM](http://go.microsoft.com/fwlink/p/?linkid=246464).  
  
```  
  
ADD r0, r8, pc         ; A2193: this instruction generates unpredictable behavior  
  
```  
  
 A2196: no se puede codificar la instrucción de 16 bits  
 No se puede codificar la instrucción especificada como una instrucción de control de 16 bits.  Especifique una instrucción de 32 bits o reorganizar el código para mostrar la etiqueta de destino en el intervalo de una instrucción de 16 bits.  
  
 El ensamblador puede intentar codificar una bifurcación de 16 bits y producir este error, incluso aunque puedan codificarse con una bifurcación de 32 bits. Puede resolver este problema mediante el uso de la `.W` especificador para marcar explícitamente la bifurcación como de 32 bits.  
  
```  
  
  ADD.N r0, r1, r2      ; A2196: instruction cannot be encoded in 16 bits  
  
  B.W label             ; OK  
  B.N label             ; A2196: instruction cannot be encoded in 16 bits  
  SPACE 10000  
label  
  
```  
  
 A2202: Sintaxis de instrucción de Pre-UAL que no se permite en la región de control  
 Código Thumb debe usar la sintaxis de lenguaje de ensamblador unificado (UAL).  Ya no se acepta la sintaxis antigua  
  
```  
  
ADDEQS r0, r1         ; A2202: Pre-UAL instruction syntax not allowed in THUMB region  
ADDSEQ r0, r1         ; OK  
  
```  
  
 A2513: Rotación debe ser un número par  
 En el modo ARM, hay una sintaxis alternativa para especificar las constantes.  En lugar de escribir `#<const>`, puede escribir `#<byte>,#<rot>`, que representa el valor constante que se obtiene el valor de la rotación `<byte>` derecha haciendo `<rot>`.  Cuando se utiliza esta sintaxis, debe realizar el valor de `<rot>` incluso.  
  
```  
  
MOV r0, #4, #2       ; OK  
MOV r0, #4, #1       ; A2513: Rotation must be even  
  
```  
  
 A2557: Número incorrecto de bytes para volver a escribir  
 En la estructura de NEÓN cargar e instrucciones de almacenamiento (`VLDn`, `VSTn`), hay una sintaxis alternativa para especificar la reescritura en el registro de base.  En lugar de colocar un signo de exclamación (!) después de la dirección, puede especificar un valor inmediato que indica el desplazamiento que se va a agregar al registro de base.  Si utiliza esta sintaxis, debe especificar el número exacto de bytes que se han cargado o almacenado por la instrucción.  
  
```  
  
VLD1.8 {d0-d3}, [r0]!         ; OK  
VLD1.8 {d0-d3}, [r0], #32     ; OK  
VLD1.8 {d0-d3}, [r0], #100    ; A2557: Incorrect number of bytes to write back  
  
```  
  
### <a name="warnings"></a>Advertencias  
 A4228: Valor de alineación supera la alineación de área; no se garantiza de alineación  
 La alineación que se especifica en un `ALIGN` directiva es mayor que la alineación de los `AREA`.  Como resultado, el ensamblador no puede garantizar que el `ALIGN` se respetará la directiva.  
  
 Para solucionar este problema, puede especificar en el `AREA` directiva un `ALIGN` atributo que es igual o mayor que la alineación deseada.  
  
```  
  
AREA |.myarea1|  
ALIGN 8           ; A4228: Alignment value exceeds AREA alignment; alignment not guaranteed  
  
AREA |.myarea2|,ALIGN=3  
ALIGN 8           ; OK  
  
```  
  
 A4508: Uso de esta constante girada está en desuso  
 En el modo ARM, hay una sintaxis alternativa para especificar las constantes.  En lugar de escribir `#<const>`, puede escribir `#<byte>,#<rot>`, que representa el valor constante que se obtiene el valor de la rotación `<byte>` derecha haciendo `<rot>`.  En algunos contextos, ARM desusado el uso de estas constantes girados. En estos casos, usar el basic `#<const>` sintaxis en su lugar.  
  
```  
  
ANDS r0, r0, #1                ; OK  
ANDS r0, r0, #4, #2            ; A4508: Use of this rotated constant is deprecated  
  
```  
  
 A4509: Este formato de instrucción condicional está en desuso  
 Este formato de instrucción condicional está en desuso por ARM en la arquitectura de ARMv8. Le recomendamos que cambie el código para usar bifurcaciones condicionales. Para ver qué instrucciones condicionales siguen siendo compatibles, consulte el [Manual de referencia de arquitectura de ARM](http://go.microsoft.com/fwlink/p/?linkid=246464).  
  
 Esta advertencia no es emite cuando el `-oldit` se utiliza el modificador de línea de comandos.  
  
```  
  
ADDEQ r0, r1, r8              ; A4509: This form of conditional instruction is deprecated  
  
```  
  
## <a name="see-also"></a>Vea también  
 [Referencia de línea de comandos de ensamblador ARM](../../assembler/arm/arm-assembler-command-line-reference.md)   
 [Directivas del ensamblador de ARM](../../assembler/arm/arm-assembler-directives.md)