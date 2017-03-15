---
title: "Directivas de preprocesamiento de archivos MAKE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "!UNDEF"
  - "!INCLUDE"
  - "!IFNDEF"
  - "!MESSAGE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "!CMDSWITCHES (directiva)"
  - "!ELSE (directiva)"
  - "!ELSEIF (directiva)"
  - "!ELSEIFDEF (directiva)"
  - "!ELSEIFNDEF (directiva)"
  - "!ENDIF (directiva)"
  - "!ERROR (directiva)"
  - "!IF (directiva)"
  - "!IFDEF (directiva)"
  - "!IFNDEF (directiva)"
  - "!INCLUDE (directiva)"
  - "!MESSAGE (directiva)"
  - "!UNDEF (directiva)"
  - "CMDSWITCHES (directiva)"
  - "directivas, preprocesamiento de archivos make"
  - "ELSE (directiva)"
  - "ELSEIF (directiva)"
  - "ELSEIFDEF (directiva)"
  - "ELSEIFNDEF (directiva)"
  - "ENDIF (directiva)"
  - "ERROR (directiva)"
  - "IF (directiva)"
  - "IFDEF (directiva)"
  - "IFNDEF (directiva)"
  - "INCLUDE (directiva)"
  - "Make (archivos), preprocesar directivas"
  - "MESSAGE (directiva)"
  - "NMAKE (programa), expresiones"
  - "NMAKE (programa), directivas de preprocesador"
  - "preprocesar directivas, Make (archivos)"
  - "UNDEF (directiva)"
ms.assetid: bcedeccb-d981-469d-b9e8-ab5d097fd8c2
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Directivas de preprocesamiento de archivos MAKE
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las directivas de preprocesamiento no distinguen entre mayúsculas y minúsculas.  El signo de exclamación de cierre \(\!\) debe aparecer al comienzo de la línea.  Puede haber varios espacios o tabulaciones, o ninguno, a continuación del signo de exclamación para aplicar sangría.  
  
 **\!CMDSWITCHES**  
 {**\+**&#124; **–**}*opción*...  Activa o desactiva cada argumento *option* enumerado.  Los espacios o tabulaciones deben estar delante del operador \+ o –; no pueden estar entre el operador y las [letras de opción](../build/nmake-options.md).  Las letras no distinguen entre mayúsculas y minúsculas, y se especifican sin una barra oblicua \(\/\).  Para activar unas opciones y desactivar otras, se han de utilizar especificaciones independientes de **\!CMDSWITCHES**.  
  
 Sólo \/D, \/I, \/N y \/S se pueden usar en un archivo MAKE.  En Tools.ini, están permitidas todas las opciones excepto \/F, \/HELP, \/NOLOGO, \/X y \/?.  Los cambios especificados en un bloque de descripción no tienen efecto hasta el siguiente bloque de descripción.  Esta directiva actualiza **MAKEFLAGS**; los cambios se heredan durante la recursividad si se especifica **MAKEFLAGS**.  
  
 **\!ERROR**  *texto*  
 Muestra *text* en el error U1050 y después interrumpe NMAKE, aunque se utilicen \/K, \/I, **.IGNORE**, **\!CMDSWITCHES** o el modificador de comando guión \(–\).  Los espacios o tabulaciones delante de *text* se omiten.  
  
 **\!MESSAGE**  *texto*  
 Muestra *text* para la salida estándar.  Los espacios o tabulaciones delante de *text* se omiten.  
  
 *nombre de archivo de* **\!include**\[ **\<**\] \[ **\>**\]  
 Lee *filename* como un archivo MAKE y después continúa con el archivo MAKE actual.  Búsquedas de NMAKE para *el nombre de archivo* primero en de forma recursiva especificado o actual el directorio, recorre los directorios de cualquier archivo MAKE primarios, a continuación, si *el nombre de archivo* está incluido entre corchetes angulares \(\< \>\), en los directorios especificados por la macro de **include** , que se establece inicialmente a la variable de entorno INCLUDE.  Es útil para pasar valores de **.SUFFIXES**, **.PRECIOUS** y reglas de inferencia a los archivos MAKE recursivos.  
  
 **\!IF**  `constantexpression`  
 Procesa instrucciones entre **\!IF** y la siguiente instrucción **\!ELSE** o `!ENDIF` si `constantexpression` se evalúa como un valor distinto de cero.  
  
 **\!IFDEF**  *nombreDeMacro*  
 Procesa instrucciones entre `!IFDEF` y la siguiente instrucción **\!ELSE** o `!ENDIF` si el argumento *macroname* está definido.  Una macro nula se considera que está definida.  
  
 **\!IFNDEF**  *nombreDeMacro*  
 Procesa instrucciones entre **\!IFNDEF** y la siguiente instrucción **\!ELSE** o `!ENDIF` si el argumento *macroname* no está definido.  
  
 **\!ELSE**\[**IF** *expresiónConstante* &#124; **IFDEF** *nombreDeMacro*&#124; **IFNDEF** *nombreDeMacro*\]  
 Procesa instrucciones entre **\!ELSE** y la siguiente instrucción `!ENDIF` si la instrucción **\!IF**, `!IFDEF` o **\!IFNDEF** anterior se evalúa como cero.  Las palabras clave opcionales ofrecen un control de preprocesamiento superior.  
  
 **\!ELSEIF**  
 Sinónimo de **\!ELSE IF**.  
  
 **\!ELSEIFDEF**  
 Sinónimo de **\!ELSE IFDEF**.  
  
 **\!ELSEIFNDEF**  
 Sinónimo de **\!ELSE IFNDEF**.  
  
 `!ENDIF`  
 Marca el final de un bloque **\!IF**, `!IFDEF` o **\!IFNDEF**.  El texto que sigue a continuación de `!ENDIF` en la misma línea se omite.  
  
 **\!UNDEF**  *nombreDeMacro*  
 Deja sin definir *macroname*.  
  
## Vea también  
 [Preprocesamiento de archivos MAKE](../build/makefile-preprocessing.md)