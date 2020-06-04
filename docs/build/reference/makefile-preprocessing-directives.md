---
title: Directivas de preprocesamiento de archivos MAKE
ms.date: 08/11/2019
f1_keywords:
- '!UNDEF'
- '!INCLUDE'
- '!IFNDEF'
- '!MESSAGE'
helpviewer_keywords:
- ERROR directive
- '!MESSAGE directive'
- IF directive
- '!UNDEF directive'
- IFDEF directive
- '!ELSEIF directive'
- '!IFDEF directive'
- '!IF directive'
- UNDEF directive
- '!CMDSWITCHES directive'
- ENDIF directive
- directives, makefile preprocessing
- INCLUDE directive
- IFNDEF directive
- preprocessing directives, makefiles
- '!IFNDEF directive'
- ELSEIFNDEF directive
- NMAKE program, expressions
- ELSEIF directive
- '!ERROR directive'
- '!ENDIF directive'
- MESSAGE directive
- '!INCLUDE directive'
- '!ELSEIFNDEF directive'
- CMDSWITCHES directive
- '!ELSEIFDEF directive'
- '!ELSE directive'
- NMAKE program, preprocessor directives
- makefiles, preprocessing directives
- ELSE directive
- ELSEIFDEF directive
ms.assetid: bcedeccb-d981-469d-b9e8-ab5d097fd8c2
ms.openlocfilehash: 1dd30c8e338343626d8a8cc3157d118e44f0ea18
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170493"
---
# <a name="makefile-preprocessing-directives"></a>Directivas de preprocesamiento de archivos MAKE

Las directivas de preprocesamiento no distinguen mayúsculas de minúsculas. El signo de exclamación inicial (!) debe aparecer al principio de la línea. Pueden aparecer cero o más espacios o tabulaciones después del signo de exclamación para la sangría.

- `!CMDSWITCHES` la &#124; *opción* {`+` `-`}...

   Activa o desactiva cada *opción* . Los espacios o las tabulaciones deben aparecer antes del operador `+` o `-`; no puede aparecer ninguno entre el operador y las [Letras de opción](running-nmake.md#nmake-options). Las letras no distinguen mayúsculas de minúsculas y se especifican sin una barra diagonal (`/`). Para activar algunas opciones y desactivar otras, use especificaciones independientes de `!CMDSWITCHES`.

   Solo se pueden usar/D,/I,/N y/S en un archivo make. En Tools. ini, se permiten todas las opciones excepto/F,/HELP,/NOLOGO,/X y/?. Los cambios especificados en un bloque de descripción no surtirán efecto hasta el siguiente bloque de descripción. Esta directiva actualiza **MAKEFLAGS**; los cambios se heredan durante la recursividad si se especifica **MAKEFLAGS** .

- `!ERROR` *texto*

   Muestra el *texto* en U1050 de error y, a continuación, detiene NMAKE, aunque se use/K,/i, `.IGNORE`, `!CMDSWITCHES`o el modificador de comando dash (`-`). Se omiten los espacios o las tabulaciones antes del *texto* .

- `!MESSAGE` *texto*

   Muestra *texto* en la salida estándar. Se omiten los espacios o las tabulaciones antes del *texto* .

- `!INCLUDE` [`<`] *nombreDeArchivo* [`>`]

   Lee el *nombre de archivo* como un archivo make y continúa con el archivo MAKE actual. NMAKE busca primero el *nombre de archivo* en el directorio especificado o actual, de forma recursiva a través de los directorios de cualquier archivo make primario y, a continuación, si *filename* está incluido entre corchetes angulares (`< >`), en los directorios especificados por la macro **include** , que se establece inicialmente en la variable de entorno include. Resulta útil para pasar `.SUFFIXES` valores de configuración, `.PRECIOUS`y reglas de inferencia a archivos make recursivos.

- `!IF` *constant_expression*

   Procesa instrucciones entre `!IF` y el `!ELSE` o `!ENDIF` siguiente si *constant_expression* se evalúa como un valor distinto de cero.

- `!IFDEF` *nombremacro*

   Procesa instrucciones entre `!IFDEF` y el `!ELSE` o `!ENDIF` siguiente si se define *nombremacro* . Se considera que se ha definido una macro null.

- `!IFNDEF` *nombremacro*

   Procesa instrucciones entre `!IFNDEF` y el `!ELSE` siguiente o `!ENDIF` si *nombremacro* no está definido.

- `!ELSE` [`IF` *constant_expression* &#124; `IFDEF` *nombremacro* &#124; `IFNDEF` *nombremacro*]

   Procesa instrucciones entre `!ELSE` y el `!ENDIF` siguiente si la instrucción `!IF`, `!IFDEF`o `!IFNDEF` anterior se evaluó como cero. Las palabras clave opcionales proporcionan un mayor control del preprocesamiento.

- `!ELSEIF`

   Sinónimo para `!ELSE IF`.

- `!ELSEIFDEF`

   Sinónimo para `!ELSE IFDEF`.

- `!ELSEIFNDEF`

   Sinónimo para `!ELSE IFNDEF`.

- `!ENDIF`

   Marca el final de un bloque de `!IF`, `!IFDEF`o `!IFNDEF`. Se omite cualquier texto después de `!ENDIF` en la misma línea.

- `!UNDEF` *nombremacro*

   Anula la definición de *nombremacro*.

## <a name="see-also"></a>Consulte también

- [Preprocesamiento de archivos MAKE](makefile-preprocessing.md)
