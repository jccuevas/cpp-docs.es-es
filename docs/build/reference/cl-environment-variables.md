---
title: "Variables de entorno de CL | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cl.exe (compilador), variables de entorno"
  - "variables de entorno, compilador CL"
  - "INCLUDE (variable de entorno)"
  - "LIBPATH (variable de entorno)"
ms.assetid: 2606585b-a681-42ee-986e-1c9a2da32108
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Variables de entorno de CL
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La herramienta CL usa las siguientes variables de entorno:  
  
-   CL y \_CL\_, si se definen.  La herramienta CL antepone las opciones y los argumentos definidos en la variable de entorno de CL a los argumentos de la línea de comandos, y anexa las opciones y los argumentos definidos en \_CL\_ antes del procesamiento.  
  
-   INCLUDE, que debe señalar al subdirectorio \\include de la instalación de Visual C\+\+.  
  
-   LIBPATH, que especifica los directorios en los que se van a buscar archivos de metadatos a los que se hace referencia con [\#using](../../preprocessor/hash-using-directive-cpp.md).  Para obtener más información sobre LIBPATH, vea `#using`.  
  
 Puede establecer la variable de entorno de CL o \_CL\_ usando la sintaxis siguiente:  
  
```  
SET CL=[ [option] ... [file] ...] [/link link-opt ...]  
SET _CL_=[ [option] ... [file] ...] [/link link-opt ...]  
```  
  
 Para obtener más información sobre los argumentos de las variables de entorno de CL y \_CL\_, consulte [Sintaxis de línea de comandos del compilador](../../build/reference/compiler-command-line-syntax.md).  
  
 Puede usar estas variables de entorno para definir los archivos y las opciones que usa con más frecuencia, y puede usar la línea de comandos para definir archivos y opciones específicos para fines específicos.  Las variables de entorno de CL y \_CL\_ están limitadas a 1024 caracteres \(el límite de entrada de la línea de comandos\).  
  
 No puede usar la opción \/D para definir un símbolo que use un signo igual \(\=\).  Puede sustituir el signo de número \(\#\) por un signo igual.  De este modo, puede usar las variables de entorno de CL o \_CL\_ para definir constantes de preprocesador con valores explícitos, como `/DDEBUG #1` para definir `DEBUG=1`.  
  
 Para obtener información relacionada, vea [Establecer variables de entorno](../../build/setting-the-path-and-environment-variables-for-command-line-builds.md).  
  
## Ejemplos  
 A continuación se muestra un ejemplo de cómo establecer la variable de entorno de CL:  
  
```  
SET CL=/Zp2 /Ox /I\INCLUDE\MYINCLS \LIB\BINMODE.OBJ  
```  
  
 Cuando se establece esta variable de entorno, si escribe `CL INPUT.C` en la línea de comandos, este es el comando eficaz:  
  
```  
CL /Zp2 /Ox /I\INCLUDE\MYINCLS \LIB\BINMODE.OBJ INPUT.C  
```  
  
 En el ejemplo siguiente, un comando de CL sin formato compila los archivos de código fuente FILE1.c y FILE2.c y, a continuación, vincula los archivos objeto FILE1.obj, FILE2.obj y FILE3.obj:  
  
```  
SET CL=FILE1.C FILE2.C  
SET _CL_=FILE3.OBJ  
CL  
  
```  
  
 Esto tiene el mismo efecto que la línea de comandos siguiente:  
  
```  
CL FILE1.C FILE2.C FILE3.OBJ  
```  
  
## Vea también  
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)