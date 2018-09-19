---
title: Período de duración | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- local variables, lifetime
- variables, automatic
- storage classes, lifetime
- variables, lifetime
- automatic storage class
- automatic storage class, duration
- storage class specifiers, storage duration
- memory allocation, dynamic allocation
- functions [C++], lifetime
- storage duration
- dynamic memory allocation
- memory allocation, dynamic
- lifetime
- global variables, lifetime
ms.assetid: ff0b42cb-3f0f-49a3-a94f-d1d825d8ddfe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 34873681d0bc33cede9cda994aa9684e04a689e4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46113778"
---
# <a name="lifetime"></a>Período de duración

La "duración" es el período durante la ejecución de un programa en el que una variable o una función existe. La duración del almacenamiento del identificador determina su duración.

Un identificador declarado con el elemento *storage-class-specifier* **static** tiene una duración de almacenamiento estática. Los identificadores con duración de almacenamiento estática (también denominada "global") tienen un almacenamiento y un valor definido para la duración de un programa. Se reserva el almacenamiento y el valor almacenado del identificador se inicializa una sola vez, antes del inicio del programa. Un identificador declarado con vinculación externa o interna también tiene una duración de almacenamiento estática (vea [Vinculación](../c-language/linkage.md)).

Un identificador declarado sin el especificador de clase de almacenamiento **static** tiene una duración de almacenamiento automática si se declara dentro de una función. Un identificador con la duración de almacenamiento automática (un "identificador local") tiene un almacenamiento y un valor definido únicamente en el bloque donde se define o se declara el identificador. A un identificador automático se le asigna nuevo almacenamiento cada vez que el programa entra en ese bloque y pierde el almacenamiento (y el valor) cuando el programa sale del bloque. Los identificadores declarados en una función sin vinculación también tienen una duración de almacenamiento automática.

Las reglas siguientes especifican si un identificador tiene duración global (estática) o local (automática):

- Todas las funciones tienen una duración estática. Por consiguiente, existen en todo momento durante la ejecución del programa. Los identificadores declarados en el nivel externo (es decir, fuera de todos los bloques del programa en el mismo nivel de definiciones de función) siempre tienen una duración global (estática).

- Si una variable local tiene un inicializador, se inicializa cada vez que se crea (a menos que se declare como **static**). Los parámetros de función también tienen una duración local. Se puede especificar la duración global para un identificador dentro de un bloque si se incluye el especificador de clase de almacenamiento **static** en su declaración. Una vez declarada como **static**, la variable mantiene su valor desde una entrada del bloque hasta la siguiente.

Aunque un identificador con una duración global existe a lo largo de la ejecución del programa de origen (por ejemplo, una variable declarada externamente o una variable local declarada con la palabra clave **static**), puede no estar visible en todas las partes del programa. Vea [Ámbito y visibilidad](../c-language/scope-and-visibility.md) para obtener información sobre la visibilidad y vea [Clases de almacenamiento](../c-language/c-storage-classes.md) para obtener una descripción del elemento *storage-class-specifier* no terminal.

La memoria se puede asignar según sea necesario (dinámicamente) si se crea mediante el uso de rutinas de biblioteca especiales como `malloc`. Puesto que la asignación de memoria dinámica utiliza las rutinas de biblioteca, no se considera parte del lenguaje. Vea la función [malloc](../c-runtime-library/reference/malloc.md) en la *Referencia de la biblioteca en tiempo de ejecución*.

## <a name="see-also"></a>Vea también

[Duración, ámbito, visibilidad y vinculación](../c-language/lifetime-scope-visibility-and-linkage.md)