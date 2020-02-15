---
title: Ejecutar NMAKE
description: Guía de referencia de las opciones de la línea de comandos de Microsoft NMAKE.
ms.date: 02/09/2020
helpviewer_keywords:
- targets, building
- response files, NMAKE
- targets
- command files
- NMAKE program, targets
- NMAKE program, running
- command files, NMAKE
ms.assetid: 0421104d-8b7b-4bf3-86c1-928d9b7c1a8c
ms.openlocfilehash: bfada33a89c04d25bf7444cbf3b1e7ef3ed44385
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257601"
---
# <a name="running-nmake"></a>Ejecutar NMAKE

## <a name="syntax"></a>Sintaxis

> **NMake** [*opción* ...] [*macros* ...] [*destinos* ...] [ **\@** _archivo de comandos_ ...]

## <a name="remarks"></a>Observaciones

NMAKE solo compila los *destinos* especificados o, cuando no se especifica ninguno, el primer destino del archivo make. El primer destino del archivo make puede ser un [pseudodestino](description-blocks.md#pseudotargets) que compila otros destinos. NMAKE usa archivos make especificados con **/f**o si no se especifica **/f** , el archivo make en el directorio actual. Si no se especifica ningún archivo make, usa reglas de inferencia para compilar los *destinos*de la línea de comandos.

El archivo de texto del *archivo de comandos* (o el archivo de respuesta) contiene la entrada de la línea de comandos. Otras entradas pueden preceder o seguir \@*archivo de comandos*. Se permite una ruta de acceso. En *el archivo de comandos*, los saltos de línea se tratan como espacios. Incluya las definiciones de macro entre comillas si contienen espacios.

## <a name="nmake-options"></a>Opciones de NMAKE

En la tabla siguiente se describen las opciones de NMAKE. Las opciones van precedidas de una barra diagonal (`/`) o un guión (`-`) y no distinguen mayúsculas de minúsculas. Utilice [`!CMDSWITCHES`](makefile-preprocessing-directives.md) para cambiar la configuración de las opciones en un archivo make o en Tools. ini.

| Opción | Propósito |
| ------------ | ------------- |
| **/A** | Fuerza la compilación de todos los destinos evaluados, incluso si no están actualizados en comparación con los dependientes. No fuerza la compilación de destinos no relacionados. |
| **B** | Fuerza la compilación incluso si las marcas de tiempo son iguales. Solo se recomienda para los sistemas rápidos (resolución de dos segundos o menos). |
| **/C** | Suprime la salida predeterminada, incluidos errores o advertencias NMAKE no graves, marcas de tiempo y un mensaje de copyright de NMAKE. Suprime las advertencias emitidas por **/k**. |
| **/D** | Muestra las marcas de tiempo de cada destino evaluado y dependiente, y un mensaje cuando no existe un destino. Útil con **/p** para depurar un archivo make. Use `!CMDSWITCHES` para establecer o borrar **/d** para parte de un archivo make. |
| **/E** | Hace que las variables de entorno invaliden las definiciones de macro de archivos make. |
| **/errorreport** [ **ninguno** &#124; **-solicitar** &#124; **envío** de **cola** &#124; ] | En desuso. La configuración de [Informe de errores de Windows (WER)](/windows/win32/wer/windows-error-reporting) controla los informes. |
| **/F** *nombre de archivo* | Especifica el *nombre de archivo* como un archivo make. Los espacios o las pestañas pueden preceder al *nombre de archivo*. Especifique **/f** una vez para cada archivo make. Para proporcionar un archivo make a partir de la entrada estándar, especifique un guión (`-`) para el *nombre de archivo*y finalice la entrada del teclado con **F6** o **Ctrl + Z**. |
| **/G** | Muestra los archivos make incluidos con la Directiva de `!INCLUDE`. Para obtener más información, vea [directivas de preprocesamiento de archivos make](makefile-preprocessing-directives.md). |
| **/Help**, **/?** | Muestra un breve resumen de la sintaxis de línea de comandos de NMAKE. |
| **/I** | Omite los códigos de salida de todos los comandos. Para establecer o borrar **/i** para parte de un archivo make, use `!CMDSWITCHES`. Para omitir los códigos de salida de una parte de un archivo make, use un modificador de comando Dash (`-`) o [`.IGNORE`](dot-directives.md). Invalida **/k** si se especifican ambos. |
| **/K** | Continúa compilando dependencias no relacionadas, si un comando devuelve un error. También emite una advertencia y devuelve un código de salida de 1. De forma predeterminada, NMAKE se detiene si algún comando devuelve un código de salida distinto de cero. Las advertencias de **/k** se suprimen en **/c**; **/I** invalida **/k** si se especifican ambos. |
| **/N** | Muestra pero no ejecuta comandos; los comandos de preprocesamiento se ejecutan. No muestra comandos en llamadas NMAKE recursivas. Resulta útil para depurar archivos make y comprobar las marcas de tiempo. Para establecer o borrar **/n** para parte de un archivo make, use `!CMDSWITCHES`. |
| **/NOLOGO** | Suprime el mensaje de copyright de NMAKE. |
| **/P** | Muestra información (definiciones de macro, reglas de inferencia, destinos, lista de [`.SUFFIXES`](dot-directives.md) ) a la salida estándar y, a continuación, ejecuta la compilación. Si no existe ningún archivo make o destino de línea de comandos, solo muestra información. Use with **/d** para depurar un archivo make. |
| **/Q** | Comprueba las marcas de tiempo de los destinos; no ejecuta la compilación. Devuelve un código de salida cero si todos los destinos están actualizados y un código de salida distinto de cero si algún destino no está actualizado. Los comandos de preprocesamiento se ejecutan. Resulta útil cuando se ejecuta NMAKE desde un archivo por lotes. |
| **/R** | Borra la lista de `.SUFFIXES` y omite las reglas de inferencia y las macros que se definen en el archivo Tools. ini o que están predefinidas. |
| **Modificado** | Suprime la presentación de comandos ejecutados. Para suprimir la presentación en parte de un archivo make, use el modificador de comando **\@** o [`.SILENT`](dot-directives.md). Para establecer o borrar **/s** para parte de un archivo make, use `!CMDSWITCHES`. |
| **/T** | Actualiza las marcas de tiempo de los destinos de la línea de comandos (o el primer destino del archivo make) y ejecuta los comandos de preprocesamiento, pero no ejecuta la compilación. |
| **/U** | Debe usarse junto con **/n**. Vuelca archivos NMAKE en línea para que se pueda usar la salida **/n** como un archivo por lotes. |
| **/X** *nombreDeArchivo* | Envía la salida de error de NMAKE al *nombre de archivo* en lugar de a un error estándar. Los espacios o las pestañas pueden preceder al *nombre de archivo*. Para enviar la salida de errores a la salida estándar, especifique un guión (`-`) para el *nombre de archivo*. No afecta a la salida de los comandos al error estándar. |
| **/Y** | Deshabilita las reglas de inferencia del modo por lotes. Cuando se selecciona esta opción, todas las reglas de inferencia en modo por lotes se tratan como reglas de inferencia normales. |

## <a name="toolsini-and-nmake"></a>Tools.ini y NMAKE

NMAKE Lee Tools. ini antes de leer los archivos make, a menos que se utilice **/r** . Busca Tools. ini en primer lugar en el directorio actual y, después, en el directorio especificado por la variable de entorno INIT. La sección para la configuración de NMAKE en el archivo de inicialización comienza con `[NMAKE]` y puede contener cualquier información de archivos make. Especifique un Comentario en una línea independiente empezando por un signo de número (`#`).

## <a name="exit-codes-from-nmake"></a>Códigos de salida de NMAKE

NMAKE devuelve los siguientes códigos de salida:

| Código | Significado |
| ---------- | ------------- |
| 0 | Sin errores (posiblemente una advertencia) |
| 1 | Compilación incompleta (solo se emite cuando se usa **/k** ) |
| 2 | Error de programa, posiblemente debido a uno de estos problemas:<br /> -Un error de sintaxis en el archivo make<br /> -Un código de error o de salida de un comando<br /> -Una interrupción por parte del usuario |
| 4 | Error del sistema: memoria insuficiente |
| 255 | El destino no está actualizado (solo se emite cuando se usa **/q** ) |

## <a name="see-also"></a>Consulte también

[Referencia de NMAKE](nmake-reference.md)
