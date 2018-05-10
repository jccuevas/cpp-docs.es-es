---
title: Ámbito y visibilidad | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- scope, levels
- visibility
- file scope [C++]
ms.assetid: a019eb7c-66ed-46a7-bc9f-89a963930a56
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b85f0ca180fc60b1281440845289d2f2a39d71af
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="scope-and-visibility"></a>Ámbito y visibilidad
La "visibilidad" de un identificador determina las partes del programa en las que se puede hacer referencia a él (su "ámbito"). Un identificador está visible (es decir, se puede utilizar) solo en las partes de un programa enmarcado por su "ámbito", que se puede limitar (en orden de restricción creciente) al archivo, función, bloque o prototipo de función en que aparece. El ámbito de un identificador es la parte del programa en que se puede usar el nombre. Esto a veces se denomina "ámbito léxico". Hay cuatro tipos de ámbito: función, archivo, bloque y prototipo de función.  
  
 Todos los identificadores, excepto las etiquetas, tienen su ámbito determinado por el nivel en el que se produce la declaración. Las reglas siguientes para cada clase de ámbito determinan la visibilidad de los identificadores dentro de un programa:  
  
 Ámbito de archivo  
 El declarador o el especificador de tipo de un identificador con ámbito de archivo aparece fuera de un bloque o una lista de parámetros y es accesible desde cualquier lugar de la unidad de traducción después de su declaración. Los identificadores con ámbito de archivo suelen denominarse "global" o "externo". El ámbito de un identificador global comienza en el momento de su definición o declaración y finaliza al final de la unidad de traducción.  
  
 Ámbito de función  
 Una etiqueta es la única clase de identificador que tiene ámbito de función. Una etiqueta se declara implícitamente por su uso en una instrucción. Los nombres de etiqueta deben ser únicos dentro de una función. (Para más información sobre las etiquetas y los nombres de etiqueta, vea [Instrucciones goto y con etiquetas](../c-language/goto-and-labeled-statements-c.md)).  
  
 Ámbito de bloque  
 El declarador o el especificador de tipo de un identificador con ámbito de bloque aparece dentro de un bloque o dentro de la lista de declaraciones de parámetros formales de una definición de función. Solo es visible desde el momento de su declaración o definición hasta el final del bloque que contiene su declaración o definición. Su ámbito se limita a ese bloque y los bloques anidados en ese bloque y termina en la llave de cierre del bloque asociado. Dichos identificadores se denominan a veces "variables locales".  
  
 Ámbito de prototipo de función  
 El declarador o el especificador de tipo de un identificador con ámbito de prototipo de función aparece en la lista de declaraciones de parámetros en un prototipo de función (no es parte de la declaración de función). Su ámbito finaliza al final del declarador de función.  
  
 Las declaraciones apropiadas para que las variables sean visibles en otros archivos de código fuente se describen en [Clases de almacenamiento](../c-language/c-storage-classes.md). Sin embargo, las variables y las funciones declaradas en el nivel externo con el especificador de clase de almacenamiento **static** solo son visibles dentro del archivo de código fuente en que se definen. Todas la demás funciones son visibles globalmente.  
  
## <a name="see-also"></a>Vea también  
 [Duración, ámbito, visibilidad y vinculación](../c-language/lifetime-scope-visibility-and-linkage.md)