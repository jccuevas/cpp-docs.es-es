---
title: Opciones de NMAKE
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, options
ms.assetid: 00ba1aec-ef27-44cf-8d82-c5c095e45bae
ms.openlocfilehash: 84130afea6cc73c480b46f065d6d85e365101b38
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50455346"
---
# <a name="nmake-options"></a>Opciones de NMAKE

Opciones de NMAKE se describen en la tabla siguiente. Las opciones van precedidas por una barra diagonal (/) o un guión (-) y no distinguen mayúsculas de minúsculas. Use [! CMDSWITCHES](../build/makefile-preprocessing-directives.md) para cambiar la configuración de opciones en un archivo MAKE o en Tools.ini.

|Opción|Propósito|
|------------|-------------|
|/A|Fuerza la generación de todos los destinos evaluados, aunque no estén actualizados con respecto a los elementos dependientes. No fuerza la compilación de destinos no relacionados.|
|/B|Fuerza la generación incluso si las marcas de tiempo son iguales. Se recomienda sólo para sistemas muy rápidos (resolución de dos segundos o menos).|
|/C|Suprime la salida predeterminada, incluidos los errores NMAKE recuperables o advertencias, las marcas de tiempo y mensaje de copyright de NMAKE. Suprime las advertencias emitidas por/k.|
|/D|Muestra las marcas de tiempo de cada destino evalúan y dependiente y un mensaje cuando un destino no existe. Resulta útil con /P para depurar un archivo MAKE. Use **! CMDSWITCHES** para establecer o borrar /D para parte de un archivo MAKE.|
|/E|Hace que las variables de entorno reemplazar las definiciones de macro de archivo MAKE.|
|/ ERRORREPORT [NONE &AMP;#124; PROMPT &AMP;#124; COLA &AMP;#124; ENVÍO]|Si se produce un error en nmake.exe en tiempo de ejecución, puede utilizar/errorReport para enviar información a Microsoft sobre estos errores internos.<br /><br /> Para obtener más información sobre/errorreport, vea [/errorReport (informar de errores de compilador interno)](../build/reference/errorreport-report-internal-compiler-errors.md).|
|/F *nombre de archivo*|Especifica *filename* como un archivo MAKE. Pueden preceder los espacios o tabulaciones *filename*. Especificar /F una vez para cada archivo MAKE. Para proporcionar un archivo MAKE de entrada estándar, especificar un guión (-) para *filename*y terminar la entrada del teclado con F6 o CTRL + Z.|
|/ G|Muestra los archivos MAKE incluidos con el. #INCLUDE (directiva).  Consulte [directivas de preprocesamiento de archivos MAKE](../build/makefile-preprocessing-directives.md) para obtener más información.|
|¿/ AYUDA, /?|Muestra un breve resumen de sintaxis de línea de comandos de NMAKE.|
|/I|Omite los códigos de salida de todos los comandos. Para establecer o borrar /I para parte de un archivo MAKE, utilice **! CMDSWITCHES**. Para omitir los códigos de salida para parte de un archivo MAKE, use un modificador de comandos de guión (-) o [. OMITIR](../build/dot-directives.md). Invalida /K si se especifican ambos.|
|/K|Continúa la generación de dependencias no relacionadas, si un comando devuelve un error. También emite una advertencia y devuelve un código de salida de 1. De forma predeterminada, NMAKE se detiene si algún comando devuelve un código de salida distinto de cero. Se suprimen las advertencias de /K por /C; /I invalida /K si se especifican ambos.|
|/N|Muestra, pero no ejecuta comandos; se ejecutan comandos de preprocesamiento. No muestra los comandos en llamadas recursivas a NMAKE. Es útil para la depuración de archivos MAKE y la comprobación de las marcas de tiempo. Para establecer o borrar /N para parte de un archivo MAKE, utilice **! CMDSWITCHES**.|
|/NOLOGO|Suprime el mensaje de copyright de NMAKE.|
|/P|Muestra información (definiciones de macro, reglas de inferencia, destinos, [. SUFIJOS](../build/dot-directives.md) lista) en la salida estándar, y, a continuación, se ejecuta la compilación. Si no existe ningún archivo MAKE o el destino de línea de comandos, muestra solo la información. Utilícelo con /D para depurar un archivo MAKE.|
|/Q|Marcas de tiempo de comprobaciones de destinos; no se ejecuta la compilación. Devuelve un cero código de salida si todos los destinos están actualizados y un código de salida distinto de cero si no es de cualquier destino. Se ejecutan comandos de preprocesamiento. Resulta útil cuando se ejecuta NMAKE desde un archivo por lotes.|
|/R|Borra la **. SUFIJOS** lista y omite las reglas de inferencia y macros que se definen en el archivo Tools.ini o que están predefinidos.|
|/S|Suprime la presentación de los comandos ejecutados. Para suprimir la presentación en parte de un archivo MAKE, utilice el **\@** modificador de comandos o [. SILENCIOSA](../build/dot-directives.md). Para establecer o borrar /S para parte de un archivo MAKE, utilice **! CMDSWITCHES**.|
|/T|Actualiza las marcas de tiempo de destinos de línea de comandos (o el primer destino de archivo MAKE) y ejecuta comandos de preprocesamiento, pero no se ejecuta la compilación.|
|/U|Debe usarse junto con/n. Vuelca archivos NMAKE en línea para que la salida /N puede usarse como un archivo por lotes.|
|/X *nombre de archivo*|Envía la salida de errores NMAKE para *filename* en lugar de error estándar. Pueden preceder los espacios o tabulaciones *filename*. Para enviar la salida de error en la salida estándar, especificar un guión (-) para *filename*. No afecta a la salida de comandos a error estándar.|
|/Y|Deshabilita las reglas de inferencia de modo por lotes. Cuando se selecciona esta opción, todas las reglas de inferencia de modo por lotes se tratan como reglas de inferencia regulares.|

## <a name="see-also"></a>Vea también

[Ejecución de NMAKE](../build/running-nmake.md)
