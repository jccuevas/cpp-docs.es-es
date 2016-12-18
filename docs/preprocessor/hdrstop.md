---
title: "hdrstop | Microsoft Docs"
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
  - "hdrstop_CPP"
  - "vc-pragma.hdrstop"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "hdrstop (pragma)"
  - "pragma (directivas), hdrstop"
ms.assetid: 5ea8370a-10d1-4538-ade6-4c841185da0e
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# hdrstop
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Proporciona control adicional sobre los nombres de archivo de la precompilación y sobre la ubicación en la que se guarda el estado de la compilación.  
  
## Sintaxis  
  
```  
  
#pragma hdrstop [( "filename" )]    
```  
  
## Comentarios  
 El elemento *filename* es el nombre del archivo de encabezado precompilado que se va a usar o crear \(dependiendo de si se especifica [\/Yu](../build/reference/yu-use-precompiled-header-file.md) o [\/Yc](../build/reference/yc-create-precompiled-header-file.md)\).  Si *filename* no contiene una especificación de ruta, se presupone que el archivo de encabezado precompilado está en el mismo directorio que el archivo de código fuente.  
  
 Si un archivo de C o C\+\+ contiene una instrucción pragma **hdrstop** cuando se compila con \/Yc, el compilador guarda el estado de la compilación hasta el lugar donde se encuentra la instrucción pragma.  El estado compilado del código que aparece detrás de la instrucción pragma no se guarda.  
  
 Use *filename* para designar el archivo de encabezado precompilado en el que se guarda el estado compilado.  El espacio entre **hdrstop** y *filename* es opcional.  El nombre de archivo especificado en la instrucción pragma **hdrstop** es una cadena y, por tanto, está sujeto a las restricciones de cualquier cadena de C o C\+\+.  En concreto, debe incluirse entre comillas y usar el carácter de escape \(la barra diagonal inversa\) para especificar nombres de directorio.  Por ejemplo:  
  
```  
#pragma hdrstop( "c:\\projects\\include\\myinc.pch" )  
```  
  
 El nombre del archivo de encabezado precompilado se determina según las reglas siguientes, en orden de prioridad:  
  
1.  El argumento de la opción del compilador \/Fp  
  
2.  El argumento de *filename* de \#**pragma hdrstop**  
  
3.  El nombre base del archivo de código fuente con una extensión .PCH  
  
 Para las opciones \/Yc y \/Yu, si ninguna de las dos opciones de compilación ni la instrucción pragma **hdrstop** especifican un nombre de archivo, el nombre base del archivo de código fuente se utiliza como el nombre base del archivo de encabezado precompilado.  
  
 Puede usar también comandos de preprocesamiento para realizar la sustitución de macros del modo siguiente:  
  
```  
#define INCLUDE_PATH "c:\\progra~`1\\devstsu~1\\vc\\include\\"  
#define PCH_FNAME "PROG.PCH"  
.  
.  
.  
#pragma hdrstop( INCLUDE_PATH PCH_FNAME )  
```  
  
 Las siguientes reglas determinan dónde se puede colocar la instrucción pragma **hdrstop**:  
  
-   Debe aparecer fuera de cualquier declaración o definición de datos o función.  
  
-   Se debe especificar en el archivo de código fuente, no en un archivo de encabezado.  
  
## Ejemplo  
  
```  
#include <windows.h>                 // Include several files  
#include "myhdr.h"  
  
__inline Disp( char *szToDisplay )   // Define an inline function  
{  
    ...                              // Some code to display string  
}  
#pragma hdrstop  
```  
  
 En este ejemplo, la instrucción pragma **hdrstop** aparece después de que se hayan incluido dos archivos y se haya definido una función insertada.  Esto podría parecer, a primera vista, una colocación extraña de una instrucción pragma.  Tenga en cuenta, sin embargo, que el uso de las opciones de precompilación manual, \/Yc y \/Yu, con la instrucción pragma **hdrstop** permite que se precompilen los archivos de código fuente en su totalidad, incluido el código insertado.  El compilador de Microsoft no le limita a precompilar solo las declaraciones de datos.  
  
## Vea también  
 [Directives pragma y la palabra clave \_\_pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)