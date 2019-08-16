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
ms.openlocfilehash: 4825ca180cb1b419a9ffa5232575ba1a24f8805d
ms.sourcegitcommit: db1ed91fa7451ade91c3fb76bc7a2b857f8a5eef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/13/2019
ms.locfileid: "68980510"
---
# <a name="makefile-preprocessing-directives"></a>Directivas de preprocesamiento de archivos MAKE

Las directivas de preprocesamiento no distinguen mayúsculas de minúsculas. El signo de exclamación inicial (!) debe aparecer al principio de la línea. Pueden aparecer cero o más espacios o tabulaciones después del signo de exclamación para la sangría.

- `!CMDSWITCHES``+` *opción* { &#124; }...`-`

   Activa o desactiva cada *opción* . Los espacios o las tabulaciones deben `+` aparecer `-` delante del operador OR; no puede aparecer ninguno entre el operador y las [Letras de opción](running-nmake.md#nmake-options). Las letras no distinguen mayúsculas de minúsculas y se`/`especifican sin una barra diagonal (). Para activar algunas opciones y desactivar otras, use especificaciones independientes de `!CMDSWITCHES`.

   Solo se pueden usar/D,/I,/N y/S en un archivo make. En Tools. ini, se permiten todas las opciones excepto/F,/HELP,/NOLOGO,/X y/?. Los cambios especificados en un bloque de descripción no surtirán efecto hasta el siguiente bloque de descripción. Esta directiva actualiza **MAKEFLAGS**; los cambios se heredan durante la recursividad si se especifica **MAKEFLAGS** .

- `!ERROR`*texto* de

   Muestra el *texto* en error U1050 y, a continuación, detiene NMAKE, aunque se use `.IGNORE`/k `!CMDSWITCHES`,/i,, o`-`el modificador de comando Dash (). Se omiten los espacios o las tabulaciones antes del *texto* .

- `!MESSAGE`*texto* de

   Muestra *texto* en la salida estándar. Se omiten los espacios o las tabulaciones antes del *texto* .

- `!INCLUDE`[ `<` ] *nombre* de `>` archivo []

   Lee el *nombre de archivo* como un archivo make y continúa con el archivo MAKE actual. NMAKE busca primero el *nombre de archivo* en el directorio especificado o actual, de forma recursiva a través de los directorios de cualquier archivo make primario y, a continuación, si *filename* está entre corchetes angulares (`< >`), en los directorios especificados por el parámetro  **INCLUIR** macro, que se establece inicialmente en la variable de entorno include. Resulta útil para `.SUFFIXES` pasar la `.PRECIOUS`configuración, y las reglas de inferencia a los archivos make recursivos.

- `!IF`*constant_expression*

   Procesa instrucciones entre `!IF` y la siguiente `!ELSE` o `!ENDIF` si *constant_expression* se evalúa como un valor distinto de cero.

- `!IFDEF`*nombremacro*

   Procesa las instrucciones `!IFDEF` entre y el `!ELSE` siguiente `!ENDIF` o si se define *nombremacro* . Se considera que se ha definido una macro null.

- `!IFNDEF`*nombremacro*

   Procesa instrucciones entre `!IFNDEF` y la siguiente `!ELSE` o `!ENDIF` si *nombremacro* no está definido.

- `!ELSE`[`IF` &#124; *constant_expression* &#124; *nombremacro* nombremacro] `IFDEF` `IFNDEF`

   Procesa instrucciones entre `!ELSE` y el siguiente `!ENDIF` si la instrucción `!IF`, `!IFDEF`o `!IFNDEF` anterior se evaluó como cero. Las palabras clave opcionales proporcionan un mayor control del preprocesamiento.

- `!ELSEIF`

   Sinónimo para `!ELSE IF`.

- `!ELSEIFDEF`

   Sinónimo para `!ELSE IFDEF`.

- `!ELSEIFNDEF`

   Sinónimo para `!ELSE IFNDEF`.

- `!ENDIF`

   Marca el final de un `!IF`bloque `!IFDEF`, o `!IFNDEF` . Cualquier texto después `!ENDIF` de en la misma línea se omite.

- `!UNDEF`*nombremacro*

   Anula la definición de *nombremacro*.

## <a name="see-also"></a>Vea también

- [Preprocesamiento de archivos MAKE](makefile-preprocessing.md)