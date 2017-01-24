---
title: "Informaci&#243;n general sobre LIB | Microsoft Docs"
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
  - "Lib"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LIB [C++], modos"
ms.assetid: e997d423-f574-434f-8b56-25585d137ee0
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Informaci&#243;n general sobre LIB
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

LIB crea bibliotecas estándar, bibliotecas de importación y archivos de exportación que puede utilizar con [LINK](../../build/reference/linker-options.md) al compilar un programa.  Se ejecuta en el símbolo del sistema.  
  
 Puede utilizar esta herramienta al:  
  
-   [Compilar o modificar una biblioteca COFF](../../build/reference/managing-a-library.md)  
  
-   [Extraer un objeto miembro a un archivo](../../build/reference/extracting-a-library-member.md)  
  
-   [Crear un archivo de exportación y una biblioteca de importación](../../build/reference/working-with-import-libraries-and-export-files.md)  
  
 Estos modos son mutuamente exclusivos; sólo puede usar LIB en un modo cada vez.  
  
## Opciones de LIB  
 La siguiente tabla muestra las opciones de lib.exe, con un vínculo a más información.  
  
 **\/DEF**  
 Crea una biblioteca de importación y un archivo de exportación.  
  
 Para obtener más información, vea [Compilar bibliotecas de importación y archivos de exportación](../../build/reference/building-an-import-library-and-export-file.md).  
  
 **\/ERRORREPORT**  
 Envía información a Microsoft sobre los errores internos de lib.exe.  
  
 Para obtener más información, vea [Ejecutar LIB](../../build/reference/running-lib.md).  
  
 **\/EXPORT**  
 Exporta una función del programa.  
  
 Para obtener más información, vea [Compilar bibliotecas de importación y archivos de exportación](../../build/reference/building-an-import-library-and-export-file.md).  
  
 **\/EXTRACT**  
 Crea un archivo objeto \(.obj\) que contiene una copia de un miembro de una biblioteca existente.  
  
 Para obtener más información, vea [Extraer un miembro de biblioteca](../../build/reference/extracting-a-library-member.md).  
  
 **\/INCLUDE**  
 Agrega un símbolo a la tabla de símbolos.  
  
 Para obtener más información, vea [Compilar bibliotecas de importación y archivos de exportación](../../build/reference/building-an-import-library-and-export-file.md).  
  
 **\/LIBPATH**  
 Reemplaza la ruta de la biblioteca de entorno.  
  
 Para obtener más información, vea [Administrar una biblioteca](../../build/reference/managing-a-library.md).  
  
 **\/LIST**  
 Muestra información sobre la biblioteca de salida en la salida estándar.  
  
 Para obtener más información, vea [Administrar una biblioteca](../../build/reference/managing-a-library.md).  
  
 **\/LTCG**  
 Hace que se genere la biblioteca mediante compilación de código en tiempo de vínculo.  
  
 Para obtener más información, vea [Ejecutar LIB](../../build/reference/running-lib.md).  
  
 **\/MACHINE**  
 Especifica la plataforma de destino del programa.  
  
 Para obtener más información, vea [Ejecutar LIB](../../build/reference/running-lib.md).  
  
 **\/NAME**  
 Al compilar una biblioteca de importación, especifica el nombre del archivo DLL para el que se va a compilar dicha biblioteca.  
  
 Para obtener más información, vea [Administrar una biblioteca](../../build/reference/managing-a-library.md).  
  
 **\/NODEFAULTLIB**  
 Quita una o más bibliotecas predeterminadas de la lista de bibliotecas en las que se busca al resolver referencias externas.  
  
 Para obtener más información, vea [Administrar una biblioteca](../../build/reference/managing-a-library.md).  
  
 **\/NOLOGO**  
 Suprime la presentación del mensaje con información de copyright y de versión de LIB, e impide que se repitan los archivos de comandos.  
  
 Para obtener más información, vea [Ejecutar LIB](../../build/reference/running-lib.md).  
  
 **\/OUT**  
 Reemplaza el nombre de archivo de salida predeterminado.  
  
 Para obtener más información, vea [Administrar una biblioteca](../../build/reference/managing-a-library.md).  
  
 **\/REMOVE**  
 Omite un objeto de la biblioteca de resultados.  
  
 Para obtener más información, vea [Administrar una biblioteca](../../build/reference/managing-a-library.md).  
  
 **\/SUBSYSTEM**  
 Indica al sistema operativo la forma de ejecutar un programa creado mediante vinculación con la biblioteca de resultados.  
  
 Para obtener más información, vea [Administrar una biblioteca](../../build/reference/managing-a-library.md).  
  
 **\/VERBOSE**  
 Muestra detalles sobre el progreso de la sesión, incluidos los nombres de los archivos .obj que se agregan.  
  
 Para obtener más información, vea [Ejecutar LIB](../../build/reference/running-lib.md).  
  
 **\/WX**  
 Trata las advertencias como errores.  
  
 Para obtener más información, vea [Ejecutar LIB](../../build/reference/running-lib.md).  
  
## Vea también  
 [Referencia de LIB](../../build/reference/lib-reference.md)   
 [Archivos de entrada de LIB](../../build/reference/lib-input-files.md)   
 [Archivos de resultados de LIB](../../build/reference/lib-output-files.md)   
 [Otros resultados de LIB](../../build/reference/other-lib-output.md)   
 [Estructura de una biblioteca](../../build/reference/structure-of-a-library.md)