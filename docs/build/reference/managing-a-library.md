---
title: "Administrar una biblioteca | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLibrarianTool.IgnoreAllDefaultLibraries"
  - "VC.Project.VCLibrarianTool.AdditionalDependencies"
  - "VC.Project.VCLibrarianTool.RemoveObjects"
  - "VC.Project.VCLibrarianTool.LibraryPaths"
  - "VC.Project.VCLibrarianTool.OutputFile"
  - "VC.Project.VCLibrarianTool.IgnoreDefaultLibraryNames"
  - "VC.Project.VCLibrarianTool.AdditionalLibraryDirectories"
  - "VC.Project.VCLibrarianTool.ListContentsFile"
  - "VC.Project.VCLibrarianTool.ListContents"
  - "VC.Project.VCLibrarianTool.SubSystemVersion"
  - "VC.Project.VCLibrarianTool.IgnoreDefaultLibraryName"
  - "VC.Project.VCLibrarianTool.SubSystem"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/CONVERT (opción del administrador de bibliotecas)"
  - "/LIBPATH (opción del administrador de bibliotecas)"
  - "/LINK50COMPAT (opción del administrador de bibliotecas)"
  - "/LIST (opción del administrador de bibliotecas)"
  - "/OUT (opción del administrador de bibliotecas)"
  - "/REMOVE (opción del administrador de bibliotecas)"
  - "/SUBSYSTEM (opción del administrador de bibliotecas)"
  - "CONVERT (opción del administrador de bibliotecas)"
  - "-CONVERT (opción del administrador de bibliotecas)"
  - "LIB [C++], administrar bibliotecas COFF"
  - "LIBPATH (opción del administrador de bibliotecas)"
  - "-LIBPATH (opción del administrador de bibliotecas)"
  - "LINK50COMPAT (opción del administrador de bibliotecas)"
  - "-LINK50COMPAT (opción del administrador de bibliotecas)"
  - "LIST (opción del administrador de bibliotecas)"
  - "-LIST (opción del administrador de bibliotecas)"
  - "archivos objeto"
  - "archivos objeto, compilar y modificar"
  - "OUT (opción del administrador de bibliotecas)"
  - "-OUT (opción del administrador de bibliotecas)"
  - "REMOVE (opción del administrador de bibliotecas)"
  - "-REMOVE (opción del administrador de bibliotecas)"
  - "SUBSYSTEM (opción del administrador de bibliotecas)"
  - "-SUBSYSTEM (opción del administrador de bibliotecas)"
ms.assetid: f56a8b85-fbdc-4c09-8d8e-00f0ffe1da53
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Administrar una biblioteca
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El modo predeterminado de LIB es compilar o modificar una biblioteca de objetos en formato COFF.  LIB se ejecutará en este modo cuando no especifique \/EXTRACT \(para copiar un objeto en un archivo\) o \/DEF \(para compilar una biblioteca de importación\).  
  
 Para compilar una biblioteca a partir de objetos o bibliotecas, utilice la sintaxis siguiente:  
  
```  
LIB [options...] files...  
```  
  
 Este comando crea una biblioteca a partir de uno o más archivos de entrada.  Los archivos pueden ser archivos objeto en formato COFF, archivos objeto en formato OMF de 32 bits o bibliotecas COFF existentes.  LIB crea una biblioteca que contiene todos los objetos en los archivos especificados.  Si un archivo de entrada es un archivo objeto en formato OMF de 32 bits, LIB lo convierte a formato COFF antes de compilar la biblioteca.  LIB no puede aceptar un objeto en formato OMF de 32 bits perteneciente a una biblioteca creada por la versión de 16 bits de LIB.  Primero debe utilizar la herramienta LIB de 16 bits para extraer el objeto; después puede utilizar el archivo objeto extraído como entrada de la herramienta LIB de 32 bits.  
  
 De manera predeterminada, LIB utiliza como nombre para el archivo de salida el nombre base del primer objeto o archivo de biblioteca, y le asigna la extensión .lib.  El archivo de salida se coloca en el directorio actual.  Si ya existe un archivo con el mismo nombre, el archivo de salida reemplazará el archivo existente.  Para conservar una biblioteca existente, utilice la opción \/OUT para especificar un nombre para el archivo de salida.  
  
 Al compilar y modificar una biblioteca puede utilizar las siguientes opciones:  
  
 \/LIBPATH: `dir`  
 Reemplaza la ruta de la biblioteca de entorno.  Para obtener información detallada, vea la descripción de la opción [\/LIBPATH](../../build/reference/libpath-additional-libpath.md) de LINK.  
  
 \/LIST  
 Muestra información sobre la biblioteca de salida en la salida estándar.  La salida se puede redirigir a un archivo.  Puede usar \/LIST para determinar el contenido de una biblioteca existente sin modificarlo.  
  
 \/NAME: *filename*  
 Al compilar una biblioteca de importación, especifica el nombre del archivo DLL para el que se va a compilar dicha biblioteca.  
  
 \/NODEFAULTLIB  
 Quita una o más bibliotecas predeterminadas de la lista de bibliotecas en las que se busca al resolver referencias externas.  Para obtener más información, vea [\/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md).  
  
 \/OUT: *filename*  
 Reemplaza el nombre de archivo de salida predeterminado.  De manera predeterminada, la biblioteca de resultados se crea en el directorio actual, con el nombre base de la primera biblioteca o el primer archivo objeto con la extensión .lib en la línea de comandos.  
  
 \/REMOVE: *object*  
 Omite el objeto especificado \(*object*\) de la biblioteca de resultados.  LIB crea una biblioteca de salida; para ello, combina todos los objetos \(independientemente de que estén en archivos objeto o bibliotecas\) y, a continuación, elimina los objetos especificados con \/REMOVE.  
  
 \/SUBSISTEMA: {CONSOLA &#124; EFI\_APPLICATION &#124; EFI\_BOOT\_SERVICE\_DRIVER &#124; EFI\_ROM &#124; EFI\_RUNTIME\_DRIVER &#124; NATIVO &#124; POSIX &#124; WINDOWS &#124; WINDOWSCE } \[, \#\[. \#\#\]\]  
 Indica al sistema operativo la forma de ejecutar un programa creado mediante vinculación con la biblioteca de resultados.  Para obtener más información, vea la descripción de la opción [\/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md) de LINK.  
  
 En las opciones de LIB especificadas en la línea de comandos no se distingue mayúsculas de minúsculas.  
  
 Puede utilizar LIB para realizar las siguientes tareas de administración de biblioteca:  
  
-   Para agregar objetos a una biblioteca, especifique el nombre de archivo para la biblioteca existente y los nombres de archivo para los nuevos objetos.  
  
-   Para combinar bibliotecas, especifique los nombres de archivo de las bibliotecas.  Puede agregar objetos y combinar bibliotecas con un único comando LIB.  
  
-   Para reemplazar un miembro de biblioteca con un objeto nuevo, especifique la biblioteca que contiene el objeto miembro que se va a reemplazar y el nombre de archivo para el nuevo objeto \(o la biblioteca que lo contiene\).  Cuando existe un objeto con el mismo nombre en más de un archivo de entrada, LIB coloca el último objeto especificado en el comando LIB en la biblioteca de resultados.  Cuando reemplace un miembro de biblioteca, asegúrese de especificar el nuevo objeto o la nueva biblioteca después de la biblioteca que contiene el objeto antiguo.  
  
-   Para eliminar un miembro de una biblioteca, utilice la opción \/REMOVE.  LIB procesa las especificaciones de \/REMOVE existentes después de combinar todos los objetos de entrada, independientemente del orden que tengan en la línea de comandos.  
  
> [!NOTE]
>  No puede eliminar un miembro y extraerlo a un archivo en un mismo paso.  Primero deberá extraer el objeto miembro mediante la opción \/EXTRACT y después ejecutar LIB de nuevo, con la opción \/REMOVE.  Este comportamiento difiere del de la herramienta LIB de 16 bits \(para las bibliotecas OMF\) proporcionada en otros productos de Microsoft.  
  
## Vea también  
 [Referencia de LIB](../../build/reference/lib-reference.md)