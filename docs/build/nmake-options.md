---
title: "Opciones de NMAKE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "NMAKE (programa), opciones"
ms.assetid: 00ba1aec-ef27-44cf-8d82-c5c095e45bae
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Opciones de NMAKE
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las opciones de NMAKE se describen en la tabla siguiente.  Las opciones van precedidas de una barra oblicua \(\/\) o de un guión \(–\) y no distinguen entre mayúsculas y minúsculas.  Se ha de utilizar [\!CMDSWITCHES](../build/makefile-preprocessing-directives.md) para cambiar los valores de opciones en un archivo MAKE o en Tools.ini.  
  
|Opción|Objetivo|  
|------------|--------------|  
|\/A|Fuerza la compilación de todos los destinos evaluados, aunque no estén actualizados con respecto a los dependientes.  No fuerza la compilación de destinos no relacionados.|  
|\/B|Fuerza la compilación aunque las marcas de tiempo sean iguales.  Sólo se recomienda para sistemas muy rápidos \(resolución de dos segundos o inferior\).|  
|\/C|Suprime la salida predeterminada, incluidos los errores o advertencias de NMAKE no graves, las marcas de tiempo y el mensaje de copyright de NMAKE.  Suprime las advertencias emitidas mediante \/K.|  
|\/D|Muestra marcas de tiempo de cada dependiente y destino evaluado, y un mensaje cuando no existe un destino.  Es útil con \/P para la depuración de un archivo MAKE.  Usa **\!CMDSWITCHES** para establecer o desactivar \/D para parte de un archivo MAKE.|  
|\/E|Provoca que las variables de entorno reemplacen las definiciones de macro de archivos MAKE.|  
|\/ERRORREPORT\[NONE &#124; PROMPT &#124; QUEUE &#124; SEND \]|Si en nmake.exe se produce un error en tiempo de ejecución, puede utilizar \/ERRORREPORT para enviar información a Microsoft sobre estos errores internos.<br /><br /> Para obtener más información sobre \/ERRORREPORT, vea [\/errorReport \(Informar de los errores del compilador\)](../build/reference/errorreport-report-internal-compiler-errors.md).|  
|\/F `filename`|Especifica `filename` como un archivo Make.  Delante de `filename` puede haber espacios o tabulaciones.  Se ha de especificar \/F una vez para cada archivo MAKE.  Para proporcionar un archivo MAKE de entrada estándar, se ha de especificar un guión \(–\) para `filename`, y finalizar mediante una acción del teclado con F6 o con CTRL\+Z.|  
|\/G|Muestra los archivos MAKE incluidos con la directiva \!INCLUDE.  Vea [Directivas de preprocesamiento de archivos MAKE](../build/makefile-preprocessing-directives.md) para obtener más información.|  
|\/HELP, \/?|Muestra un breve resumen de la sintaxis de la línea de comandos de NMAKE.|  
|\/I|Omite los códigos de salida de todos los comandos.  Usa **\!CMDSWITCHES** para establecer o desactivar \/I para parte de un archivo MAKE.  Para omitir códigos de salida para parte de un archivo MAKE, se ha de utilizar un modificador de comandos guión \(–\) o [.IGNORE](../build/dot-directives.md).  Reemplaza a \/K si se especifican ambos.|  
|\/K|Continúa la compilación de dependencias no relacionadas si un comando devuelve un error.  También emite una advertencia y devuelve un código de salida de 1.  De forma predeterminada, NMAKE se detiene si algún comando devuelve un código de salida distinto de cero.  Las advertencias de \/K se suprimen mediante \/C; \/I reemplaza a \/K si se especifican ambos.|  
|\/N|Muestra comandos pero no los ejecuta; los comandos de preprocesamiento se ejecutan.  No muestra comandos en llamadas recursivas a NMAKE.  Es útil para la depuración de archivos MAKE y la comprobación de marcas de tiempo.  Usa **\!CMDSWITCHES** para establecer o desactivar \/N para parte de un archivo MAKE.|  
|\/NOLOGO|Suprime el mensaje de copyright de NMAKE.|  
|\/P|Muestra información \(definiciones de macro, reglas de inferencia, destinos, lista [.SUFFIXES](../build/dot-directives.md)\) para salidas estándar y, a continuación, ejecuta la compilación.  Si no existe ningún destino de línea de comandos o archivo MAKE, sólo muestra información.  Se utiliza con \/D para depurar un archivo MAKE.|  
|\/Q|Comprueba marcas de tiempo de destinos; no ejecuta la compilación.  Devuelve un código de salida de cero si todos los destinos están actualizados y un código de salida distinto de cero si algún destino no lo está.  Los comandos de preprocesamiento se ejecutan.  Es útil cuando se ejecuta NMAKE a partir de un archivo por lotes.|  
|\/R|Borra la lista **.SUFFIXES** y omite las reglas de inferencia y macros definidas en el archivo Tools.ini o predefinidas.|  
|\/S|Suprime la presentación de los comandos ejecutados.  Para suprimir la presentación en parte de un archivo MAKE, usa el modificador de comandos **@** o [.SILENT](../build/dot-directives.md).  Usa **\!CMDSWITCHES** para establecer o desactivar \/S para parte de un archivo MAKE.|  
|\/T|Actualiza las marcas de tiempo de destinos de línea de comandos \(o el primer destino de archivo MAKE\) y ejecuta los comandos de preprocesamiento, pero no ejecuta la compilación.|  
|\/U|Se debe usar junto con \/N.  Realiza un volcado de memoria de los archivos NMAKE insertados, de forma que el resultado de \/N se pueda utilizar como un archivo por lotes.|  
|\/X `filename`|Envía salidas de error de NMAKE a `filename` en lugar de errores estándar.  Delante de `filename` puede haber espacios o tabulaciones.  Para enviar salidas de error a salidas estándar, se ha de especificar un guión \(–\) para `filename`.  No afecta a las salidas de comandos para errores estándar.|  
|\/Y|Deshabilita las reglas de inferencia de modo por lotes.  Cuando se selecciona esta opción, todas las reglas de inferencia de modo por lotes se consideran reglas de inferencia regulares.|  
  
## Vea también  
 [Ejecutar NMAKE](../build/running-nmake.md)