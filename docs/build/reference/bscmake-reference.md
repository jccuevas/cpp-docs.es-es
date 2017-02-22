---
title: "Referencia de BSCMAKE | Microsoft Docs"
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
  - ".bsc (archivos), compilar"
  - "archivos de información de examen (.bsc), compilar"
  - "ventanas de exploración"
  - "bsc (archivos), compilar"
  - "BSCMAKE"
  - "BSCMAKE, referencia"
  - "Utilidad de mantenimiento de información de examen de Microsoft"
ms.assetid: b97ad994-1355-4809-98db-6abc12c6fb13
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# Referencia de BSCMAKE
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

> [!WARNING]
>  Aunque BSCMAKE todavía se instala con Visual Studio, el IDE ya no lo utiliza.  Desde Visual Studio 2008, la información de examen y de símbolos se almacena automáticamente en un archivo .sdf de SQL Server en la carpeta de soluciones.  
  
 La Utilidad de mantenimiento de información de examen de Microsoft \(BSCMAKE. \(EXE\) genera un archivo de información de examen \(.bsc\) a partir de archivos .sbr creados durante la compilación.  Verá un archivo de información de examen en el Examinador de objetos.  Para obtener información sobre el Examinador de objetos, vea [Explorar en el examinador de objetos](http://msdn.microsoft.com/es-es/53eb91aa-08c6-4299-8e3c-a877ae8d0c55).  
  
 Al compilar el programa, puede crear un archivo de información de examen para el programa automáticamente, usando BSCMAKE para generar el archivo.  No necesita saber cómo se ejecuta BSCMAKE si crea el archivo de información de examen en el entorno de desarrollo de Visual C\+\+.  Sin embargo, puede que desee leer este tema para comprender las opciones disponibles.  
  
 Si compila el programa fuera del entorno de desarrollo, aún puede crear un archivo .bsc personalizado que puede examinar en el entorno.  Ejecute BSCMAKE en los archivos .sbr que creó durante la compilación.  
  
> [!NOTE]
>  Puede iniciar esta herramienta solo desde el símbolo del sistema de [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)].  No puede iniciarla desde un símbolo del sistema ni desde el Explorador de archivos.  
  
 Esta sección contiene los siguientes temas:  
  
-   [Compilar archivos de información de examen: información general](../../build/reference/building-browse-information-files-overview.md)  
  
-   [Crear un archivo .bsc](../../build/reference/building-a-dot-bsc-file.md)  
  
-   [Línea de comandos de BSCMAKE](../../build/reference/bscmake-command-line.md)  
  
-   [Archivo de comandos de BSCMAKE](../../build/reference/bscmake-command-file-response-file.md)  
  
-   [Opciones de BSCMAKE](../../build/reference/bscmake-options.md)  
  
-   [Códigos de salida de BSCMAKE](../../build/reference/bscmake-exit-codes.md)  
  
## Vea también  
 [Herramientas de compilación de C\/C\+\+](../../build/reference/c-cpp-build-tools.md)