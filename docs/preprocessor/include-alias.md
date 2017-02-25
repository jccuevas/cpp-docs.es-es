---
title: "include_alias | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc-pragma.include_alias"
  - "include_alias_CPP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "include_alias (pragma)"
  - "pragma (directivas), include_alias"
ms.assetid: 3256d589-12b3-4af0-a586-199e96eabacc
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# include_alias
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Especifica que debe usarse *short\_filename* como alias para *long\_filename*.  
  
## Sintaxis  
  
```  
  
      #pragma include_alias( "  
      long_filename  
      ", "  
      short_filename  
      " )  
#pragma include_alias( <long_filename>, <short_filename> )  
```  
  
## Comentarios  
 Algunos sistemas de archivos permiten nombres de archivo de encabezado más largos que el límite de sistema de archivos FAT 8.3.  No basta con que el compilador trunque los nombres más largos a 8.3, porque los ocho primeros caracteres de los nombres de archivo de encabezado más largos pueden no ser únicos.  Siempre que el compilador encuentra la cadena *long\_filename*, la sustituye por *short\_filename* y busca en su lugar el *short\_filename* del archivo de encabezado.  Esta directiva pragma debe aparecer antes de las directivas `#include` correspondientes.  Por ejemplo:  
  
```  
// First eight characters of these two files not unique.  
#pragma include_alias( "AppleSystemHeaderQuickdraw.h", "quickdra.h" )  
#pragma include_alias( "AppleSystemHeaderFruit.h", "fruit.h" )  
  
#pragma include_alias( "GraphicsMenu.h", "gramenu.h" )  
  
#include "AppleSystemHeaderQuickdraw.h"  
#include "AppleSystemHeaderFruit.h"  
#include "GraphicsMenu.h"  
```  
  
 El alias que se esté buscando debe coincidir exactamente con la especificación, tanto en uso de mayúsculas y minúsculas, como de ortografía y comillas dobles o corchetes angulares.  La directiva pragma **include\_alias** realiza una búsqueda de coincidencia de cadenas simple en los nombres de archivo; no se realiza ninguna otra validación del nombre de archivo.  Por ejemplo, dadas las siguientes directivas,  
  
```  
#pragma include_alias("mymath.h", "math.h")  
#include "./mymath.h"  
#include "sys/mymath.h"  
```  
  
 no se realiza ninguna operación de alias \(sustitución\), ya que las cadenas del archivo de encabezado no coinciden exactamente.  Además, tampoco se sustituyen los nombres de archivo de encabezado utilizados como argumentos para las opciones del compilador \/Yu y \/Yc, o la directiva pragma **hdrstop**.  Por ejemplo, si el archivo de código fuente contiene la siguiente directiva,  
  
```  
#include <AppleSystemHeaderStop.h>  
```  
  
 la opción del compilador correspondiente debe ser  
  
```  
/YcAppleSystemHeaderStop.h  
```  
  
 Puede utilizar la directiva pragma **include\_alias** para asignar cualquier un nombre de archivo de encabezado a otro.  Por ejemplo:  
  
```  
#pragma include_alias( "api.h", "c:\version1.0\api.h" )  
#pragma include_alias( <stdio.h>, <newstdio.h> )  
#include "api.h"  
#include <stdio.h>  
```  
  
 No mezcle los nombres de archivo delimitados por comillas con los nombres de archivo entre corchetes angulares.  Por ejemplo, dadas las dos directivas **\#pragma include\_alias** anteriores, el compilador no realiza ninguna sustitución en las siguientes directivas `#include`:  
  
```  
#include <api.h>  
#include "stdio.h"  
```  
  
 Además, la directiva siguiente genera un error:  
  
```  
#pragma include_alias(<header.h>, "header.h")  // Error  
```  
  
 Observe que el nombre de archivo indicado en los mensajes de error, o como el valor de la macro **\_\_FILE\_\_** predefinida, es el nombre del archivo una vez realizada la sustitución.  Por ejemplo, después de las siguientes directivas,  
  
```  
#pragma include_alias( "VeryLongFileName.H", "myfile.h" )  
#include "VeryLongFileName.H"  
```  
  
 un error en VERYLONGFILENAME.H muestra el mensaje de error siguiente:  
  
```  
myfile.h(15) : error C2059 : syntax error  
```  
  
 Observe también que no se admite la transitividad.  Dadas las siguientes directivas,  
  
```  
#pragma include_alias( "one.h", "two.h" )  
#pragma include_alias( "two.h", "three.h" )  
#include "one.h"  
```  
  
 el compilador busca el archivo TWO.H en lugar de THREE.H.  
  
## Vea también  
 [Directives pragma y la palabra clave \_\_pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)