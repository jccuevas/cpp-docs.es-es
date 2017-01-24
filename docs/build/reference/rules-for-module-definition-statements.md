---
title: "Reglas para instrucciones de definici&#243;n de m&#243;dulos | Microsoft Docs"
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
  - ".def"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "archivos de definición de módulos"
  - "archivos de definición de módulos, sintaxis de las instrucciones"
ms.assetid: f65cd3a7-65d7-4d06-939f-a8b1ecd50f2d
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Reglas para instrucciones de definici&#243;n de m&#243;dulos
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Las siguientes reglas de sintaxis se aplican a todas las instrucciones de un archivo .def.  Otras reglas que sólo se aplican a determinadas instrucciones se describen con cada instrucción.  
  
-   En las instrucciones, palabras clave de atributos e identificadores especificados por el usuario se distingue entre mayúsculas y minúsculas.  
  
-   Los nombres largos de archivo que contienen espacios o puntos y coma \(;\) deben encerrarse entre comillas \("\).  
  
-   Utilice uno o varios espacios, tabulaciones o caracteres de nueva línea para separar una palabra clave de instrucción de sus argumentos, y para separar instrucciones entre sí.  Un signo de dos puntos \(:\) o un signo igual \(\=\) que designa un argumento está rodeado por cero o más espacios, tabulaciones o caracteres de nueva línea.  
  
-   Las instrucciones **NAME** o **LIBRARY**, si se utilizan, deben colocarse antes de todas las demás instrucciones.  
  
-   Las instrucciones **SECTIONS** y **EXPORTS** pueden aparecer varias veces en el archivo .def.  Cada instrucción puede aceptar múltiples especificaciones, que deben ir separadas por uno o varios espacios, tabulaciones o caracteres de nueva línea.  La palabra clave de la instrucción debe aparecer una vez antes de la primera especificación, y se puede repetir antes de cada especificación adicional.  
  
-   Muchas instrucciones tienen una opción de línea de comandos LINK equivalente.  Vea la descripción de la opción LINK correspondiente para obtener más información.  
  
-   Los comentarios del archivo .def se indican mediante un punto y coma \(;\) al inicio de cada línea de comentario.  Un comentario no puede compartir línea con una instrucción, pero sí puede aparecer entre especificaciones en una instrucción que ocupe varias líneas. \(**SECTIONS** y **EXPORTS** son instrucciones que ocupan varias líneas\).  
  
-   Los argumentos numéricos se especifican en base 10 o en hexadecimal.  
  
-   Si un argumento de tipo cadena coincide con una [palabra reservada](../../build/reference/reserved-words.md), deberá ir encerrado entre comillas \("\).  
  
## Vea también  
 [Archivos de definición de módulos \(.Def\)](../../build/reference/module-definition-dot-def-files.md)   
 [Frequently Asked Questions on Building](http://msdn.microsoft.com/es-es/56a3bb8f-0181-4989-bab4-a07ba950ab08)