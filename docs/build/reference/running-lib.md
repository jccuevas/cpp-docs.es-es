---
title: "Ejecutar LIB | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLibrarianTool.TargetMachine"
  - "Lib"
  - "VC.Project.VCLibrarianTool.PrintProgress"
  - "VC.Project.VCLibrarianTool.SuppressStartupBanner"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/ (archivos de comandos)"
  - "/MACHINE (opción de la plataforma de destino)"
  - "/NOLOGO (opción del administrador de bibliotecas)"
  - "/VERBOSE (opción del administrador de bibliotecas)"
  - "archivos de comandos de dos puntos"
  - "archivos de comandos"
  - "archivos de comandos, LIB"
  - "especificador de opción de guión"
  - "especificador de opción de barra diagonal"
  - "LIB [C++], ejecutar LIB"
  - "MACHINE (opción de la plataforma de destino)"
  - "-MACHINE (opción de la plataforma de destino)"
  - "NOLOGO (opción del administrador de bibliotecas)"
  - "-NOLOGO (opción del administrador de bibliotecas)"
  - "punto y coma, archivos de comandos"
  - "barra diagonal (/)"
  - "VERBOSE (opción del administrador de bibliotecas)"
  - "-VERBOSE (opción del administrador de bibliotecas)"
ms.assetid: d54f5c81-7147-4b2c-a8db-68ce6eb1eabd
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Ejecutar LIB
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Puede utilizar varias opciones de la línea de comandos para controlar LIB.  
  
## Línea de comandos de LIB  
 Para ejecutar LIB, escriba el comando `lib` seguido de las opciones y los nombres de archivo para la tarea que desea realizar con LIB.  Esta herramienta también acepta entradas de líneas de comandos en archivos de comandos \(que se describen en la siguiente sección\).  LIB no utiliza una variable de entorno.  
  
> [!NOTE]
>  Si tiene por costumbre utilizar las herramientas LINK32.exe y LIB32.exe proporcionadas con el kit de desarrollo de software de Win32 de Microsoft para Windows NT, puede que haya utilizado el comando `link32 -lib` o `lib32` para administrar bibliotecas y crear bibliotecas de importación.  Asegúrese de modificar los archivos MAKE y los archivos de procesamiento por lotes para que utilicen el comando `lib` en lugar de los comandos anteriores.  
  
## Archivos de comandos de LIB  
 Puede pasar argumentos de una línea de comandos a LIB en un archivo de comandos; para ello, utilice la siguiente sintaxis:  
  
```  
LIB @commandfile  
```  
  
 El archivo `commandfile` es un archivo de texto.  No se permite utilizar espacios ni tabuladores entre el signo @ \(arroba\) y el nombre de archivo.  No hay ninguna extensión predeterminada; debe especificar el nombre completo de archivo, incluida la extensión.  No se pueden utilizar comodines.  Se puede especificar una ruta absoluta o relativa con el nombre de archivo.  
  
 En el archivo de comandos, puede separar los argumentos mediante espacios o tabulaciones, de la misma manera que en la línea de comandos; también puede separarlos mediante caracteres de nueva línea.  Utilice un punto y coma \(;\) para marcar un comentario.  LIB omitirá todo el texto que haya desde el punto y coma hasta el final de la línea.  
  
 Puede especificar toda la línea de comandos o una parte de la misma en un archivo de comandos, y puede utilizar más de un archivo de comandos en un comando LIB.  LIB acepta la entrada de archivo de comandos como si se especificara en esa ubicación de la línea de comandos.  No se permite utilizar archivos de comandos anidados.  LIB repite el contenido de los archivos de comandos, a menos que se utilice la opción \/NOLOGO.  
  
## Utilizar las opciones de LIB  
 Una opción consta de un especificador de opción, que puede ser un guión \(–\) o una barra diagonal \(\/\), seguido por el nombre de la opción.  Los nombres de opción no pueden abreviarse.  Algunas opciones utilizan un argumento, que deberá ir precedido por dos puntos \(:\).  No se permiten espacios ni tabulaciones dentro de una especificación de opción.  Use uno o más espacios o tabulaciones para separar especificaciones de opción en la línea de comandos.  En los nombres de opción y sus palabras clave, y en los argumentos de nombre de archivo, no se distingue mayúsculas de minúsculas; en cambio, en los identificadores que se utilizan como argumentos sí se distingue mayúsculas de minúsculas.  LIB procesa las opciones en el orden especificado en la línea de comandos y en los archivos de comandos.  Si se repite una opción con distintos argumentos, tendrá prioridad el último que se va a procesar.  
  
 Las siguientes opciones se aplican a todos los modos de LIB:  
  
 \/ERRORREPORT\[NONE &#124; PROMPT &#124; QUEUE &#124; SEND \]  
 Si en lib.exe se produce un error en tiempo de ejecución, puede utilizar \/ERRORREPORT para enviar información a Microsoft sobre estos errores internos.  
  
 Para obtener más información sobre \/ERRORREPORT, vea [\/errorReport \(Informar de los errores del compilador\)](../../build/reference/errorreport-report-internal-compiler-errors.md).  
  
 \/LTCG  
 Hace que se genere la biblioteca mediante compilación de código en tiempo de vínculo.  Para obtener más información, vea [\/LTCG](../../build/reference/ltcg-link-time-code-generation.md).  
  
 \/MACHINE  
 Especifica la plataforma de destino del programa.  En general, no es necesario especificar \/MACHINE.  LIB infiere el tipo de equipo a partir de los archivos .obj.  Sin embargo, en algunas circunstancias LIB no puede determinar el tipo de equipo y emite un mensaje de error.  Si se produce un error de este tipo, especifique \/MACHINE.  En el modo \/EXTRACT, esta opción sólo se utiliza con fines de comprobación.  Utilice `lib /?` en la línea de comandos para ver los tipos de equipos disponibles.  
  
 \/NOLOGO  
 Suprime la presentación del mensaje con información de copyright y de versión de LIB, e impide que se repitan los archivos de comandos.  
  
 \/VERBOSE  
 Muestra detalles sobre el progreso de la sesión, incluidos los nombres de los archivos .obj que se agregan.  La información se envía a la salida estándar y puede redirigirse a un archivo.  
  
 \/WX\[:NO\]  
 Trata las advertencias como errores.  Para obtener más información, vea [\/WX \(Tratar advertencias del vinculador como errores\)](../../build/reference/wx-treat-linker-warnings-as-errors.md).  
  
 Las otras opciones sólo se aplican a modos específicos de LIB.  Estas opciones se tratan en las secciones en que se describen los distintos modos.  
  
## Vea también  
 [Referencia de LIB](../../build/reference/lib-reference.md)