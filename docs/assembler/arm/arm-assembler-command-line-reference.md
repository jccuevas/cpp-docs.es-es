---
title: Referencia de la línea de comandos de ARM
ms.date: 08/30/2018
ms.assetid: f7b89478-1ab5-4995-8cde-a805f0462c45
ms.openlocfilehash: f49b59a81fbe5f11c0f219d1e1fe83a4ee811c7a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62162140"
---
# <a name="arm-assembler-command-line-reference"></a>Referencia de la línea de comandos de ARM

En este artículo proporciona información de línea de comandos sobre el ensamblador de ARM Microsoft *armasm*, que compila el lenguaje de ensamblado ARMv7 Thumb en la implementación de Microsoft de formato de archivo de objeto común (COFF). El vinculador puede vincular código COFF con el código objeto generado por el ensamblador ARM o por el compilador de C, junto con las bibliotecas de objetos creados por el bibliotecario.

## <a name="syntax"></a>Sintaxis

> **armasm** [*opciones*] *sourcefile* *objectfile*
> **armasm** [*opciones*] **-o** *objectfile* *sourcefile*

### <a name="parameters"></a>Parámetros

*options*<br/>
Una combinación de cero o más de las siguientes acciones:

- **-errors** *filename*<br/>
   Redirigir los mensajes de error y advertencia para *filename*.

- **-i** *dir*[ **;** <em>dir</em>]<br/>
   Agregue los directorios especificados en la ruta de búsqueda.

- **-predefinir** *directiva*<br/>
   Especifique una directiva de establecer, SETL o conjuntos de predefinir un símbolo.<br/>
   Ejemplo: **armasm.exe-predefinir source.asm "Recuento de establecer 150"**<br/>
   Para obtener más información, consulte el [Guía de referencia del compilador ARM armasm](http://infocenter.arm.com/help/topic/com.arm.doc.dui0802b/index.html).

- **-nowarn**<br/>
   Deshabilitar todos los mensajes de advertencia.

- **-ignore** *warning*<br/>
   Deshabilitar la advertencia especificada. Para los valores posibles, vea la sección acerca de las advertencias.

- **-help**<br/>
   Imprimir el mensaje de Ayuda de línea de comandos.

- **-machine** *máquina*<br/>
   Especifique el tipo de equipo para establecer en el encabezado PE.  Los valores posibles de *máquina* son:<br/>
   **ARM**: establece el tipo de máquina en IMAGE_FILE_MACHINE_ARMNT. Este es el valor predeterminado.<br/>
   **THUMB**: establece el tipo de máquina en IMAGE_FILE_MACHINE_THUMB.

- **-oldit**<br/>
   Generar estilo ARMv7 bloques de TI.  De forma predeterminada, compatible con ARMv8 se generan bloques de TI.

- **-a través de** *nombre de archivo*<br/>
   Leer argumentos de línea de comandos adicionales de *filename*.

- **-16**<br/>
   Ensamble el origen como instrucciones de control de posición de 16 bits.  Este es el valor predeterminado.

- **-32**<br/>
   Ensamble el origen como instrucciones de ARM de 32 bits.

- **-g**<br/>
   Generar información de depuración.

- **-errorReport:** *opción*<br/>
   Especifique cómo interno ensamblador se notifican errores a Microsoft.  Los valores posibles de *opción* son:<br/>
   **Ninguno**: no enviar informes.<br/>
   **símbolo del sistema**: pedir al usuario para enviar los informes inmediatamente.<br/>
   **cola**: pedir al usuario para enviar los informes en el siguiente inicio de sesión de administrador. Este es el valor predeterminado.<br/>
   **enviar**, enviar automáticamente informes.

*sourcefile*<br/>
El nombre del archivo de origen.

*objectfile*<br/>
El nombre del archivo objeto (salida).

## <a name="remarks"></a>Comentarios

El ejemplo siguiente muestra cómo usar armasm en un escenario típico. En primer lugar, use armasm para crear un archivo de código fuente (ASM) de lenguaje de ensamblado a un archivo objeto (.obj). A continuación, usar el compilador de C de línea de comandos de CL para compilar un archivo de origen (.c) y también especificar la opción del vinculador para vincular el archivo de objeto ARM.

**armasm myasmcode.asm -o myasmcode.obj**

**CL myccode.c /link myasmcode.obj**

## <a name="see-also"></a>Vea también

[Mensajes de diagnóstico del ensamblador de ARM](../../assembler/arm/arm-assembler-diagnostic-messages.md)<br/>
[Directivas del ensamblador de ARM](../../assembler/arm/arm-assembler-directives.md)<br/>
