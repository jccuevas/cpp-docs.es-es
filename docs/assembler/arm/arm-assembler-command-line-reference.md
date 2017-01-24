---
title: "ARM Assembler Command-Line Reference | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: f7b89478-1ab5-4995-8cde-a805f0462c45
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ARM Assembler Command-Line Reference
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

En este artículo proporciona información de línea de comandos sobre el ensamblador Microsoft ARM,  *armasm*, que compila pulgar ARMv7 lenguaje de ensamblado en la implementación de Microsoft del formato de archivo de objeto común \(COFF\).  El vinculador puede vincular código COFF con código de objeto que se produce por el ensamblador de ARM o en el compilador de C, junto con las bibliotecas de objetos creados por el bibliotecario.  
  
## Sintaxis  
  
```  
armasm [[options]] sourcefile objectfile  
```  
  
```  
armasm [[options]] -o objectfile sourcefile  
```  
  
#### Parámetros  
 `options`  
 \-errores`filename`  
 Redirigir mensajes de error y advertencia para `filename`.  
  
 \-i`dir[;dir]`  
 Agregar los directorios especificados para la ruta de búsqueda.  
  
 \-definir previamente`directive`  
 Especificar una directiva SETA, SETL o conjuntos de predefinir un símbolo.  Ejemplo: **armasm.exe \-predefine "COUNT SETA 150" source.asm**.  Para obtener más información, consulte el [manual de herramientas de ensamblador de ARM](http://go.microsoft.com/fwlink/?LinkId=246102).  
  
 nowarn\-  
 Deshabilitar todos los mensajes de advertencia.  
  
 \-Omitir`warning`  
 Desactivar el aviso especificado.  Para los valores posibles, vea la sección acerca de las advertencias.  
  
 \-Ayuda  
 Imprimir el mensaje de Ayuda de línea de comandos.  
  
 \-máquina`machine`  
 Especificar el tipo de equipo para establecer en el encabezado de PE.  Los posibles valores de `machine` son:   
**ARM**: Permite definir el tipo de máquina en IMAGE\_FILE\_MACHINE\_ARMNT.  Éste es el valor predeterminado.   
**THUMB**: Permite definir el tipo de máquina en IMAGE\_FILE\_MACHINE\_THUMB.  
  
 \-oldit  
 Generar estilo ARMv7 bloques de TI.  De forma predeterminada, ARMv8\-compatible con bloques de TI se generan.  
  
 \-a través de`filename`  
 Leer argumentos de línea de comandos adicionales de `filename`.  
  
 \-16  
 Ensamblar código fuente como instrucciones de control de posición de 16 bits.  Éste es el valor predeterminado.  
  
 \-32  
 Ensamblar código fuente como instrucciones ARM de 32 bits.  
  
 \-g  
 Generar información de depuración.  
  
 \-errorReport:`option`  
 Especificar cómo interno ensamblador se informan de errores a Microsoft.  Los posibles valores de `option` son:   
**none**: No enviar informes.   
**prompt**: Pedir al usuario que envíe informes inmediatamente.   
**queue**: Pedir al usuario que envíe informes en el siguiente inicio de sesión de administrador.  Éste es el valor predeterminado.   
**send**: Enviar informes automáticamente.  
  
 `sourcefile`  
 El nombre del archivo de origen.  
  
 `objectfile`  
 El nombre del archivo objeto \(salida\).  
  
 En el ejemplo siguiente se muestra cómo utilizar armasm en un escenario típico.  En primer lugar, utilice armasm para generar un archivo de origen \(.asm\) de lenguaje ensamblador para un archivo objeto \(.obj\).  A continuación, utilizar el compilador de c de la línea de comandos de CL para compilar un archivo de origen \(.c\) y también especificar la opción del vinculador para vincular el archivo de objeto ARM.  
  
 **armasm myasmcode.asm \-o myasmcode.obj**  
  
 **cl myccode.c \/link myasmcode.obj**  
  
## Vea también  
 [ARM Assembler Diagnostic Messages](../../assembler/arm/arm-assembler-diagnostic-messages.md)   
 [ARM Assembler Directives](../../assembler/arm/arm-assembler-directives.md)