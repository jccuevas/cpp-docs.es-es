---
title: Opciones de NMAKE | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, options
ms.assetid: 00ba1aec-ef27-44cf-8d82-c5c095e45bae
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8ef3b987de737d8300f88690754456b73c946180
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="nmake-options"></a>Opciones de NMAKE
Opciones de NMAKE se describen en la tabla siguiente. Opciones de están precedidas por una barra diagonal (/) o un guión (-) y no distinguen mayúsculas de minúsculas. Utilice [! CMDSWITCHES](../build/makefile-preprocessing-directives.md) para cambiar la configuración de opciones en un archivo MAKE o en Tools.ini.  
  
|Opción|Propósito|  
|------------|-------------|  
|/A|Fuerza la generación de todos los destinos evaluados, aunque no estén actualizados con respecto a los elementos dependientes. No se fuerza la generación de destinos no relacionados.|  
|/B|Fuerza la generación aunque las marcas de tiempo son iguales. Se recomienda únicamente para los sistemas muy rápidos (resolución de dos segundos o menos).|  
|/C|Suprime la salida predeterminada, incluidos los errores NMAKE recuperables o advertencias, marcas de tiempo y mensaje de copyright de NMAKE. Suprime las advertencias emitidas mediante/k.|  
|/D|Muestra las marcas de tiempo de cada destino evalúan y dependiente y un mensaje cuando un destino no existe. Resulta útil con /P para la depuración de un archivo MAKE. Utilice **! CMDSWITCHES** para activar o desactivar /D para parte de un archivo MAKE.|  
|/E|Hace que las variables de entorno reemplazar las definiciones de macro de archivos MAKE.|  
|/ ERRORREPORT [NINGUNO &#124; SÍMBOLO DEL SISTEMA &#124; COLA &#124; ENVÍO]|Si nmake.exe se produce un error en tiempo de ejecución, puede utilizar /ERRORREPORT para enviar información a Microsoft sobre estos errores internos.<br /><br /> Para obtener más información sobre/errorreport, vea [/errorReport (informar de errores de compilador interno)](../build/reference/errorreport-report-internal-compiler-errors.md).|  
|/F`filename`|Especifica `filename` como un archivo MAKE. Pueden preceder espacios ni tabulaciones `filename`. Especificar /F una vez para cada archivo MAKE. Para proporcionar un archivo MAKE de entrada estándar, especifique un guión (-) para `filename`, una letra y terminar la entrada de teclado con F6 o con CTRL+Z.|  
|/ G|Muestra los archivos MAKE incluidos con el. INCLUDE (directiva).  Vea [directivas de preprocesamiento de archivos MAKE](../build/makefile-preprocessing-directives.md) para obtener más información.|  
|¿/ AYUDA, /?|Muestra un breve resumen de sintaxis de línea de comandos de NMAKE.|  
|/I|Omite los códigos de salida de todos los comandos. Para activar o desactivar /I para parte de un archivo MAKE, utilice **! CMDSWITCHES**. Para omitir los códigos de salida para parte de un archivo MAKE, use un modificador de comando guión (-) o [. OMITIR](../build/dot-directives.md). Reemplaza a /K si se especifican ambos.|  
|/K|Continúa la creación de dependencias no relacionadas, si un comando devuelve un error. También emite una advertencia y devuelve un código de salida de 1. De forma predeterminada, NMAKE se detiene si algún comando devuelve un código de salida distinto de cero. Las advertencias de /K se suprimen mediante/c; /I reemplaza a /K si se especifican ambos.|  
|/N|Muestra, pero no ejecuta comandos; se ejecutan comandos de preprocesamiento. No muestra comandos en llamadas recursivas a NMAKE. Es útil para la depuración de archivos MAKE y la comprobación de las marcas de tiempo. Para activar o desactivar /N para parte de un archivo MAKE, utilice **! CMDSWITCHES**.|  
|/NOLOGO|Suprime el mensaje de copyright de NMAKE.|  
|/P|Muestra información (definiciones de macro, reglas de inferencia, destinos, [. SUFIJOS](../build/dot-directives.md) lista) a la salida estándar, y, a continuación, se ejecuta la compilación. Si no existe ningún archivo MAKE o un destino de línea de comandos, muestra únicamente información. Utilícelo con /D para depurar un archivo MAKE.|  
|/ Q|Marcas de tiempo de comprobaciones de destinos; no se ejecuta la compilación. Devuelve un cero código de salida si todos los destinos están actualizados y un código de salida distinto de cero si cualquier destino no lo es. Se ejecutan comandos de preprocesamiento. Resulta útil cuando se ejecuta NMAKE desde un archivo por lotes.|  
|/ R|Borra la **. SUFIJOS** lista y omite las reglas de inferencia y macros que se definen en el archivo Tools.ini o que están predefinidos.|  
|/ S|Suprime la presentación de los comandos ejecutados. Para suprimir la presentación en parte de un archivo MAKE, utilice la  **@**  modificador de comando o [. SILENCIOSA](../build/dot-directives.md). Para establecer o borrar /S para parte de un archivo MAKE, utilice **! CMDSWITCHES**.|  
|/T|Actualiza las marcas de tiempo de destinos de línea de comandos (o el primer destino de archivo MAKE) y ejecuta los comandos de preprocesamiento, pero no se ejecuta la compilación.|  
|/U|Debe utilizarse junto con/n. Vuelca archivos NMAKE en línea para que la salida /N puede utilizarse como un archivo por lotes.|  
|/X`filename`|Envía la salida de error NMAKE a `filename` en lugar de error estándar. Pueden preceder espacios ni tabulaciones `filename`. Para enviar la salida de errores a la salida estándar, especificar un guión (-) para `filename`. No afecta a la salida de comandos en el error estándar.|  
|/Y|Deshabilita las reglas de inferencia de modo por lotes. Cuando se selecciona esta opción, todas las reglas de inferencia de modo por lotes se tratan como reglas de inferencia regulares.|  
  
## <a name="see-also"></a>Vea también  
 [Ejecución de NMAKE](../build/running-nmake.md)