---
title: Reglas para instrucciones de definición de módulo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- .def
dev_langs:
- C++
helpviewer_keywords:
- module definition files, statement syntax
- module definition files
ms.assetid: f65cd3a7-65d7-4d06-939f-a8b1ecd50f2d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3f8de42480dae9be203a132561d722c18d6952c1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="rules-for-module-definition-statements"></a>Reglas para instrucciones de definición de módulos
Las siguientes reglas sintácticas se aplican a todas las instrucciones en un archivo .def. Otras reglas que se aplican a determinadas instrucciones se describen con cada instrucción.  
  
-   Instrucciones, palabras clave de atributo y los identificadores especificados por el usuario distinguen mayúsculas de minúsculas.  
  
-   Que contiene espacios o puntos y coma (;) de nombres de archivo largos deben incluirse entre comillas (").  
  
-   Utilice uno o varios espacios, tabulaciones ni caracteres de nueva línea para separar una palabra clave de la instrucción de sus argumentos y para separar instrucciones entre sí. Dos puntos (:) o signo de igual (=) que designa un argumento está rodeado por cero o más espacios, tabulaciones o caracteres de nueva línea.  
  
-   A **nombre** o **biblioteca** instrucción, si usa, debe preceder a todas las demás instrucciones.  
  
-   El **secciones** y **exportaciones** instrucciones pueden aparecer más de una vez en el archivo .def. Cada instrucción puede tardar varias especificaciones, que deben estar separadas por uno o varios espacios, tabulaciones o caracteres de nueva línea. La palabra clave de la instrucción debe aparecer una vez antes de la primera especificación y se puede repetir antes de cada especificación adicional.  
  
-   Muchas instrucciones tienen una opción de línea de comandos de vínculo equivalente. Vea la descripción de la opción de vínculo correspondiente para obtener más detalles.  
  
-   Comentarios en el archivo .def se designan mediante un punto y coma (;) al principio de cada línea de comentario. Un comentario no puede compartir una línea con una instrucción, pero pueden aparecer entre las especificaciones en una instrucción de varias líneas. (**Secciones** y **exportaciones** son instrucciones de varias líneas.)  
  
-   Argumentos numéricos son especificado en base 10 o hexadecimal.  
  
-   Si un argumento de cadena coincide con un [palabra reservada](../../build/reference/reserved-words.md), debe incluirse entre comillas dobles (").  
  
## <a name="see-also"></a>Vea también  
 [Archivos de definición de módulos (.Def)](../../build/reference/module-definition-dot-def-files.md)  