---
title: Reglas para instrucciones de definición de módulos
ms.date: 11/04/2016
f1_keywords:
- .def
helpviewer_keywords:
- module definition files, statement syntax
- module definition files
ms.assetid: f65cd3a7-65d7-4d06-939f-a8b1ecd50f2d
ms.openlocfilehash: f6269ad2d5bf3952e485f2ca5e5d1f411c5f1e0c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62318516"
---
# <a name="rules-for-module-definition-statements"></a>Reglas para instrucciones de definición de módulos

Las siguientes reglas sintácticas se aplican a todas las instrucciones en un archivo. def. Otras reglas que se aplican a instrucciones específicas se describen con cada instrucción.

- Instrucciones, palabras clave de atributo y los identificadores especificados por el usuario distinguen mayúsculas de minúsculas.

- Que contiene espacios o punto y coma (;) de nombres de archivo largos debe incluirse entre comillas (").

- Utilice uno o varios espacios, tabulaciones o caracteres de nueva línea para separar una palabra clave de la instrucción de sus argumentos y para separar instrucciones entre sí. Dos puntos (:) o signo igual (=) que designa un argumento está rodeado por cero o más espacios, tabulaciones o caracteres de nueva línea.

- Un **nombre** o **biblioteca** instrucción, si usa, debe preceder a todas las demás instrucciones.

- El **secciones** y **exportaciones** instrucciones pueden aparecer más de una vez en el archivo. def. Cada instrucción puede tardar varias especificaciones, que deben estar separadas por uno o varios espacios, tabulaciones o caracteres de nueva línea. La palabra clave de la instrucción debe aparecer una vez antes de la primera especificación y puede repetirse antes de cada especificación adicional.

- Muchas instrucciones tienen una opción de línea de comandos equivalente de vínculo. Vea la descripción de la opción de vínculo correspondiente para obtener más detalles.

- Comentarios en el archivo .def se designan mediante un punto y coma (;) al principio de cada línea de comentario. Un comentario no puede compartir una línea con una instrucción, pero puede aparecer entre especificaciones en una instrucción multilínea. (**Secciones** y **exportaciones** son instrucciones multilíneas.)

- Los argumentos numéricos se especifican en base 10 o hexadecimal.

- Si un argumento de cadena coincide con un [palabra reservada](reserved-words.md), debe incluirse entre comillas dobles (").

## <a name="see-also"></a>Vea también

[Archivos de definición de módulos (.Def)](module-definition-dot-def-files.md)
