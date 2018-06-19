---
title: Instrucción compuesta (C) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- compound statements
- statements, compound
ms.assetid: 32d1bf86-cbbc-42a9-ba3a-1be1c6c7754c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e25bef33e374d7e0dbf97a337cb58146b05bd093
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32385730"
---
# <a name="compound-statement-c"></a>Instrucción compuesta (C)
Una instrucción compuesta (también denominada "bloque") normalmente aparece como el cuerpo de otra instrucción, como la instrucción **if**. [Declaraciones y tipos](../c-language/declarations-and-types.md) describe el formato y significado de las declaraciones que pueden aparecer en el encabezado de una instrucción compuesta.  
  
## <a name="syntax"></a>Sintaxis  
 *compound-statement*:  
 **{**  *declaration-list* opt*statement-list*opt **}**  
  
 *declaration-list*:  
 *declaration*  
  
 *declaration-list declaration*  
  
 *statement-list*:  
 s*tatement*  
  
 *statement-list statement*  
  
 Si hay declaraciones, preceden a cualquier instrucción. El ámbito de cada identificador declarado al principio de una instrucción compuesta se extiende desde su punto de declaración hasta el final del bloque. Está visible en todo el bloque, a menos que haya una declaración del mismo identificador en un bloque interno.  
  
 Los identificadores de una instrucción compuesta se supone que son **auto**, a menos que se declaren explícitamente de otra manera con **register**, **static** o `extern`, excepto las funciones, que solo pueden ser `extern`. Aunque se omita el especificador `extern` en las declaraciones de función, la función seguirá siendo `extern`.  
  
 El almacenamiento no se asigna y la inicialización no se permite si una variable o función se declara en una instrucción compuesta con la clase de almacenamiento `extern`. La declaración hace referencia a una variable externa o función definida en otra parte.  
  
 Las variables declaradas en un bloque con la palabra clave **auto** o **register** se reasignan y, si es necesario, se inicializan cada vez que se especifica la instrucción compuesta. Estas variables no se definen una vez fuera de la instrucción compuesta. Si una variable declarada dentro de un bloque tiene el atributo **static**, la variable se inicializa cuando comienza la ejecución del programa y conserva su valor en todo el programa. Vea [Clases de almacenamiento](../c-language/c-storage-classes.md) para obtener información sobre **static**.  
  
 Este ejemplo muestra una instrucción compuesta:  
  
```  
if ( i > 0 )   
{  
    line[i] = x;  
    x++;  
    i--;  
}  
```  
  
 En este ejemplo, si `i` es mayor que 0, todas las instrucciones dentro de la instrucción compuesta se ejecutan por orden.  
  
## <a name="see-also"></a>Vea también  
 [Instrucciones](../c-language/statements-c.md)