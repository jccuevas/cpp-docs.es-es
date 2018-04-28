---
title: Referencia de línea de comandos de ensamblador ARM | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
dev_langs:
- C++
ms.assetid: f7b89478-1ab5-4995-8cde-a805f0462c45
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f196b4aad76c72233c179249386dbb42960b31a6
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2018
---
# <a name="arm-assembler-command-line-reference"></a>Referencia de la línea de comandos de ensamblador de ARM
Este artículo proporciona información de línea de comandos sobre el ensamblador de ARM de Microsoft, *armasm*, que compila el lenguaje ensamblador ARMv7 Thumb en la implementación de Microsoft de formato de archivo de objeto común (COFF). El vinculador puede vincular código COFF con el código objeto generado por el ensamblador ARM o por el compilador de C, junto con bibliotecas de objetos que se crean mediante el bibliotecario.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
armasm [[options]] sourcefile objectfile  
```  
  
```  
armasm [[options]] -o objectfile sourcefile  
```  
  
#### <a name="parameters"></a>Parámetros  
 `options`  
 -errores `filename`  
 Redirigir los mensajes de error y advertencia para `filename`.  
  
 -i `dir[;dir]`  
 Agregue los directorios especificados en la ruta de acceso de búsqueda de inclusión.  
  
 -predefinir `directive`  
 Especifique una directiva NODOSUNA, SETL o conjuntos de predefinir un símbolo. Ejemplo: **armasm.exe-predefinir "COUNT NODOSUNA 150" source.asm**. Para obtener más información, consulte el [Guía de herramientas de ensamblador de ARM](http://go.microsoft.com/fwlink/p/?linkid=246102).  
  
 -nowarn  
 Deshabilitar todos los mensajes de advertencia.  
  
 -Omitir `warning`  
 Deshabilitar la advertencia especificada. Para los valores posibles, vea la sección acerca de las advertencias.  
  
 -Ayuda  
 Imprimir el mensaje de Ayuda de línea de comandos.  
  
 -machine `machine`  
 Especifique el tipo de equipo para establecer en el encabezado PE.  Valores posibles de `machine` son:  
**ARM**: establece el tipo de equipo a IMAGE_FILE_MACHINE_ARMNT. Este es el valor predeterminado.   
**THUMB**: establece el tipo de equipo a IMAGE_FILE_MACHINE_THUMB.  
  
 -oldit  
 Generar estilo ARMv7 bloques de TI.  De forma predeterminada, ARMv8 compatible se generan bloques de TI.  
  
 -a través de `filename`  
 Lea los argumentos de línea de comandos adicionales de `filename`.  
  
 -16  
 Ensamblar origen como instrucciones de Thumb de 16 bits.  Este es el valor predeterminado.  
  
 -32  
 Ensamblar origen como instrucciones de ARM de 32 bits.  
  
 -g  
 Generar información de depuración.  
  
 -errorReport: `option`  
 Especifique cómo interno ensamblador se notifican errores a Microsoft.  Valores posibles de `option` son:   
**Ninguno**: no enviar informes.   
**símbolo del sistema**: preguntar al usuario para enviar los informes inmediatamente.   
**cola**: preguntar al usuario para enviar los informes en el siguiente inicio de sesión de administrador. Este es el valor predeterminado.   
**enviar**, enviar automáticamente informes.  
  
 `sourcefile`  
 El nombre del archivo de origen.  
  
 `objectfile`  
 El nombre del archivo objeto (salida).  
  
 En el ejemplo siguiente se muestra cómo utilizar armasm en un escenario típico. En primer lugar, use armasm para generar un archivo de origen (ASM) de lenguaje de ensamblado a un archivo objeto (.obj). A continuación, usar el compilador de C de línea de comandos de CL para compilar un archivo de origen (.c) y especificar la opción del vinculador para vincular el archivo de objeto ARM.  
  
 **armasm myasmcode.asm -o myasmcode.obj**  
  
 **CL myccode.c /link myasmcode.obj**  
  
## <a name="see-also"></a>Vea también  
 [Mensajes de diagnóstico de ensamblador de ARM](../../assembler/arm/arm-assembler-diagnostic-messages.md)   
 [Directivas del ensamblador de ARM](../../assembler/arm/arm-assembler-directives.md)