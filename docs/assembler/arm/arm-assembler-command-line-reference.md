---
title: Referencia de la línea de comandos de ARM
description: Guía de referencia de las opciones de línea de comandos del ensamblador de ARM de Microsoft.
ms.date: 02/09/2020
ms.assetid: f7b89478-1ab5-4995-8cde-a805f0462c45
ms.openlocfilehash: a63273e8d21e7a28574ec79d62c15f29ee59cd50
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257384"
---
# <a name="arm-assembler-command-line-reference"></a>Referencia de la línea de comandos de ARM

En este artículo se proporciona información de línea de comandos sobre el ensamblador de ARM de Microsoft, **armasm**. **armasm** ensambla el lenguaje de ensamblado Thumb de ARMv7 en la implementación de Microsoft del formato de archivo de objeto común (COFF). El vinculador puede vincular objetos de código COFF generados por el ensamblador de ARM y el compilador de C. Puede vincular junto con las bibliotecas de objetos creadas por el bibliotecario.

## <a name="syntax"></a>Sintaxis

> **`armasm`** [*opciones*] *source_file* *object_file*\
> **`armasm`** [*opciones*] **`-o`** *object_file* *source_file*

### <a name="parameters"></a>Parámetros

*opciones*\
Una combinación de cero o más de las opciones siguientes:

- **`-errors`** *nombre de archivo*\
   Redirigir los mensajes de error y advertencia al *nombre de archivo*.

- **`-i`** *dir*[ **`;`** <em>dir</em>] \
   Agregue los directorios especificados a la ruta de búsqueda de inclusión.

- **`-predefine`** *Directiva*\
   Especifique una directiva establecer, SETL o SETS para predefinir un símbolo.
   Ejemplo: `armasm.exe -predefine "COUNT SETA 150" source.asm`\
   Para obtener más información, vea la [Guía de referencia de Armasm del compilador de ARM](http://infocenter.arm.com/help/topic/com.arm.doc.dui0802b/index.html).

- **`-nowarn`**\
   Deshabilitar todos los mensajes de advertencia.

- **`-ignore`** *ADVERTENCIA*\
   Deshabilitar la advertencia especificada. Para ver los valores posibles, consulte la sección acerca de las advertencias.

- **`-help`**\
   Imprime el mensaje de ayuda de la línea de comandos.

- **`-machine`** *máquina*\
   Especifique el tipo de equipo que se va a establecer en el encabezado PE.  Los valores posibles para el *equipo* son: \
   **ARM**: establece el tipo de equipo en IMAGE_FILE_MACHINE_ARMNT. Esta opción es la predeterminada. \
   **Thumb**: establece el tipo de equipo en IMAGE_FILE_MACHINE_THUMB.

- **`-oldit`**\
   Generar bloques de TI de estilo ARMv7.  De forma predeterminada, se generan bloques de ti compatibles con ARMv8.

- **`-via`** *nombre de archivo*\
   Lea los argumentos adicionales de la línea de comandos desde el *nombre de archivo*.

- **`-16`**\
   Ensamble el origen como instrucciones Thumb de 16 bits.  Es la opción predeterminada.

- **`-32`**\
   Ensamble el origen como instrucciones de ARM de 32 bits.

- **`-g`**\
   Generar información de depuración.

- **`-errorReport:`** *opción*\
   Esta función está en desuso. A partir de Windows Vista, los informes de errores se controlan mediante la configuración de [Informe de errores de Windows (WER)](/windows/win32/wer/windows-error-reporting) .

*source_file*\
Nombre del archivo de origen.

*object_file*\
Nombre del archivo de objeto (salida).

## <a name="remarks"></a>Observaciones

En el ejemplo siguiente se muestra cómo usar armasm en un escenario típico. En primer lugar, use armasm para compilar un archivo de origen (. asm) de lenguaje de ensamblado en un archivo de objeto (. obj). A continuación, use el compilador de línea de comandos de CL para compilar un archivo de origen (. C) y especifique también la opción del vinculador para vincular el archivo objeto ARM.

```cmd
armasm myasmcode.asm -o myasmcode.obj
cl myccode.c /link myasmcode.obj
```

## <a name="see-also"></a>Consulte también

[Mensajes de diagnóstico del ensamblador de ARM](../../assembler/arm/arm-assembler-diagnostic-messages.md)\
[Directivas de ensamblado ARM](../../assembler/arm/arm-assembler-directives.md)
