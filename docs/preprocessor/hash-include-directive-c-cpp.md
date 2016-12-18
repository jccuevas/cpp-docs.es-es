---
title: "#include (Directiva) (C/C++) | Microsoft Docs"
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
  - "#include"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "#include (directiva)"
  - "directiva include (#include)"
  - "preprocesador, directivas"
ms.assetid: 17067dc0-8db1-4f2d-b43e-ec12ecf83238
caps.latest.revision: 15
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# #include (Directiva) (C/C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Indica al preprocesador que trate el contenido de un archivo especificado como si apareciera en el programa de origen en el punto donde aparece la directiva.  
  
## Sintaxis  
  
```  
  
      #include  "path-spec"  
#include  <path-spec>  
```  
  
## Comentarios  
 Puede organizar las definiciones constantes y de macro en los archivos de inclusión y después utilizar las directivas `#include` para agregarlas a cualquier archivo de código fuente.  Los archivos de inclusión son también útiles para incorporar declaraciones de variables externas y tipos de datos complejos.  Los tipos solo se pueden definir y denominar una sola vez en un archivo de inclusión creado para ese propósito.  
  
 `path-spec` es un nombre de archivo que opcionalmente puede ir precedido de una especificación de directorio.  El nombre de archivo debe designar un archivo existente.  La sintaxis de `path-spec` depende del sistema operativo en el que se compila el programa.  
  
 Para obtener información sobre cómo hacer referencia a los ensamblados en una aplicación de C\+\+ que se compila con [\/clr](../build/reference/clr-common-language-runtime-compilation.md), vea [\#using](../preprocessor/hash-using-directive-cpp.md).  
  
 Los dos formatos de sintaxis producen el reemplazo de esa directiva por el contenido completo del archivo de inclusión especificado.  La diferencia entre los dos formatos es el orden en el que el preprocesador busca los archivos de encabezado si la ruta de acceso que se especifica está incompleta.  En la siguiente tabla se muestran las diferencias entre ambos formatos de sintaxis.  
  
|Formato de sintaxis|Acción|  
|-------------------------|------------|  
|Formato con comillas|El preprocesador realiza la búsqueda de archivos de inclusión en este orden:<br /><br /> 1.  En el mismo directorio que el archivo que contiene la instrucción `#include`.<br />2.  En los directorios de los archivos de inclusión abiertos actualmente, en el orden inverso en el que se abrieron.  La búsqueda comienza en el directorio del archivo de inclusión principal y continúa hacia arriba por los directorios de cualquier archivo de inclusión primario principal.<br />3.  A lo largo de la ruta de acceso especificada por cada opción del compilador \/I.<br />4.  A lo largo de las rutas de acceso especificadas por la variable de entorno INCLUDE.|  
|Formato con corchetes angulares|El preprocesador realiza la búsqueda de archivos de inclusión en este orden:<br /><br /> 1.  A lo largo de la ruta de acceso especificada por cada opción del compilador \/I.<br />2.  Cuando se compila desde la línea de comandos, a lo largo de las rutas de acceso especificadas por la variable de entorno INCLUDE.|  
  
 El preprocesador detiene la búsqueda en cuanto encuentra un archivo con el nombre especificado.  Si incluye una especificación completa y no ambigua de la ruta de acceso del archivo de inclusión entre comillas dobles \(" "\), el preprocesador busca solo en esa especificación de ruta y omite los directorios estándar.  
  
 Si el nombre de archivo que está entre comillas es una especificación incompleta de ruta, el preprocesador busca primero en el directorio de archivo "principal".  Un archivo principal es el archivo que contiene la directiva `#include`.  Por ejemplo, si incluye un archivo denominado `file2` en un archivo denominado `file1`, `file1` es el archivo principal.  
  
 Los archivos de inclusión pueden estar "anidados"; es decir, una directiva `#include` puede aparecer en un archivo especificado por otra directiva `#include`.  Por ejemplo, `file2` podría incluir `file3`.  En este caso, `file1` todavía sería el elemento primario de `file2` pero sería el "elemento primario principal" de `file3`.  
  
 Cuando se anidan los archivos de inclusión y cuando se compila desde la línea de comandos, la búsqueda en los directorios comienza por los directorios del archivo primario y después continúa por los directorios de cualquier archivo primario principal.  Es decir, la búsqueda comienza en relación con el directorio que contiene el origen que se procesa actualmente.  Si no se encuentra el archivo, la búsqueda se desplaza a los directorios especificados por la opción del compilador \/I.  Por último, se busca en los directorios especificados por la variable de entorno INCLUDE.  
  
 En el entorno de desarrollo, se omite la variable de entorno INCLUDE.  Para obtener información sobre cómo establecer los directorios en los que se buscan archivos de inclusión \(también se aplica a la variable de entorno LIB\), vea [VC\+\+ Directories, Projects, Options Dialog Box](http://msdn.microsoft.com/es-es/e027448b-c811-4c3d-8531-4325ad3f6e02).  
  
 Este ejemplo muestra la inclusión de archivo mediante corchetes angulares:  
  
```  
#include <stdio.h>  
```  
  
 En este ejemplo se agrega el contenido del archivo denominado STDIO.H al programa de origen.  Los corchetes angulares hacen que el preprocesador busque STDIO.H en los directorios especificados por la variable de entorno INCLUDE, después de buscar en los directorios especificados por la opción del compilador \/I.  
  
 En el ejemplo siguiente se muestra la inclusión de archivo mediante el formato con comillas:  
  
```  
#include "defs.h"  
```  
  
 En este ejemplo se agrega el contenido del archivo especificado por DEFS.H al programa de origen.  Las comillas indican que el preprocesador busca primero en el directorio que contiene el archivo de código fuente primario.  
  
 El anidamiento de archivos de inclusión puede continuar hasta 10 niveles.  Cuando se procesa `#include` con anidamiento, el preprocesador continúa insertando el archivo de inclusión envolvente en el archivo de código fuente original.  
  
 **Específicos de Microsoft**  
  
 Para buscar archivos de código fuente que se pueden incluir, el preprocesador busca primero en los directorios especificados por la opción del compilador \/I.  Si la opción \/I no está presente o produce un error, el preprocesador utiliza la variable de entorno INCLUDE para buscar cualquier archivo de inclusión dentro de los paréntesis angulares.  La variable de entorno INCLUDE y la opción del compilador \/I pueden contener varias rutas de acceso, separadas por punto y coma \(;\).  Si aparece más de un directorio como parte de la opción \/I o en la variable de entorno INCLUDE, el preprocesador los busca en el orden en que aparecen.  
  
 Por ejemplo, el comando  
  
```  
CL /ID:\MSVC\INCLUDE MYPROG.C  
```  
  
 hace que el preprocesador busque en el directorio D: \\MSVC\\INCLUDE\\ archivos de inclusión tales como STDIO.H.  Los comandos  
  
```  
SET INCLUDE=D:\MSVC\INCLUDE  
CL MYPROG.C  
```  
  
 producen el mismo efecto.  Si se produce un error en ambos conjuntos de búsquedas, se genera un error grave del compilador.  
  
 Si se especifica completamente el nombre de un archivo de inclusión con una ruta de acceso que incluye dos puntos \(por ejemplo, F:\\MSVC\\SPECIAL\\INCL\\TEST.H\), el preprocesador sigue la ruta de acceso.  
  
 Para los archivos de inclusión especificados como `#include` "`path-spec`", la búsqueda de directorio comienza con el directorio del archivo primario y después continúa por los directorios de los archivos primarios principales.  Es decir, la búsqueda comienza en relación con el directorio que contiene el archivo de código fuente que contiene la directiva `#include` que se está procesando.  Si no hay ningún archivo primario principal y no se ha encontrado el archivo, la búsqueda continúa como si el nombre de archivo estuviese entre corchetes angulares.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [Directivas de preprocesador](../preprocessor/preprocessor-directives.md)