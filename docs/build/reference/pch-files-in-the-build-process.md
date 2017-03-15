---
title: "Archivos PCH en el proceso de compilaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "pch"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".pch (archivos), proceso de compilación"
  - "Make (archivos), archivos PCH en el proceso de compilación"
  - "PCH (archivos), proceso de compilación"
ms.assetid: ebb4b368-8a11-4009-b347-01e79af02fbc
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Archivos PCH en el proceso de compilaci&#243;n
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El código de un proyecto de software se encuentra generalmente incluido en múltiples archivos de código fuente de C o C\+\+, archivos objeto, bibliotecas y archivos de encabezados.  Normalmente, existe un archivo MAKE que coordina la combinación de esos elementos en un archivo ejecutable.  La siguiente ilustración muestra la estructura de un archivo MAKE que utiliza un archivo de encabezado precompilado.  Los nombres de macro de NMAKE y los nombres de archivo que se muestran en este diagrama son coherentes con los del código de [Ejemplo de archivo MAKE para PCH](../../build/reference/sample-makefile-for-pch.md) y [Código de ejemplo para PCH](../../build/reference/example-code-for-pch.md).  
  
 La ilustración utiliza tres elementos gráficos para mostrar el flujo del proceso de compilación.  Los rectángulos con nombre representan los archivos o macros; las tres macros representan uno o varios archivos.  Las áreas sombreadas representan las acciones de compilación o vinculación.  Las flechas muestran qué archivos y macros se combinan durante el proceso de compilación o vinculación.  
  
 ![Archivo MAKE que utiliza un archivo de encabezado precompilado](../../build/reference/media/vc30ow1.png "vc30OW1")  
Estructura de un archivo MAKE que utiliza un archivo de encabezado precompilado  
  
 En la parte superior del diagrama, STABLEHDRS y BOUNDRY son macros de NMAKE en las que se indican archivos que probablemente no necesitan volver a compilarse.  Estos archivos se compilan mediante el comando  
  
```  
CL /c /W3 /Yc$(BOUNDRY) applib.cpp myapp.cpp  
```  
  
 sólo si el archivo de encabezado precompilado \(STABLE.pch\) no existe o si se realizan cambios en los archivos indicados en las dos macros.  En cualquier caso, el archivo de encabezado precompilado sólo incluirá código de los archivos indicados en la macro STABLEHDRS.  Indique el último archivo que desee precompilar en la macro BOUNDRY.  
  
 Los archivos que se indican en estas macros pueden ser archivos de encabezado o archivos de código fuente de C o C\+\+. \(No se puede utilizar un único archivo .pch con módulos de C y con módulos de C\+\+.\) Observe que es posible utilizar la macro **hdrstop** para detener la precompilación en algún punto del archivo BOUNDRY.  Vea [hdrstop](../../preprocessor/hdrstop.md) para obtener más información.  
  
 Más abajo en el diagrama, APPLIB.obj representa el código auxiliar utilizado en la aplicación final.  Se crea a partir de APPLIB.cpp, los archivos indicados en la macro UNSTABLEHDRS y el código precompilado del encabezado precompilado.  
  
 MYAPP.obj representa la aplicación final.  Se crea a partir de MYAPP.cpp, los archivos indicados en la macro UNSTABLEHDRS y el código precompilado del encabezado precompilado.  
  
 Por último, el archivo ejecutable \(MYAPP.EXE\) se crea vinculando los archivos indicados en la macro OBJS \(APPLIB.obj y MYAPP.obj\).  
  
 Encontrará más explicaciones de la ilustración en:  
  
-   [Ejemplo de archivo MAKE para PCH](../../build/reference/sample-makefile-for-pch.md)  
  
-   [Código de ejemplo para PCH](../../build/reference/example-code-for-pch.md)  
  
## Vea también  
 [Utilizar encabezados precompilados en un proyecto](../../build/reference/using-precompiled-headers-in-a-project.md)