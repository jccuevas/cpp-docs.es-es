---
title: Resumen de reglas de ámbito
ms.date: 11/04/2016
helpviewer_keywords:
- class scope [C++], rules
- classes [C++], scope
- class names [C++], scope rules
- names [C++], class
- scope [C++], class names
ms.assetid: 47e26482-0111-466f-b857-598c15d05105
ms.openlocfilehash: af708fd72904fb775ff1088948972bec159816c6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62266912"
---
# <a name="summary-of-scope-rules"></a>Resumen de reglas de ámbito

El uso de un nombre debe ser inequívoco dentro de su ámbito (hasta el punto en que se determina la sobrecarga). Si el nombre indica una función, la función no debe ser ambigua respecto al número y tipo de parámetros. Si el nombre se mantiene no ambiguo, [acceso a miembros](../cpp/member-access-control-cpp.md) se aplican las reglas.

## <a name="constructor-initializers"></a>Inicializadores del constructor

[Los inicializadores de constructor](constructors-cpp.md#member_init_list) se evalúan en el ámbito de bloque más externo del constructor para el que se especifican. Por lo tanto, pueden usar los nombres de parámetro del constructor.

## <a name="global-names"></a>Nombres globales

Un nombre de un objeto, una función o un enumerador es global si se presenta fuera de cualquier función o clase o está precedido por el operador unario global de ámbito (`::`) y si no se usa junto con alguno de estos operadores binarios:

- Resolución de ámbito (`::`)

- Selección de miembro para objetos y referencias (**.**)

- Selección de miembro para punteros (**->**)

## <a name="qualified-names"></a>Nombres completos

Los nombres utilizados con el operador binario de resolución de ámbito (`::`) se denominan “nombres completos”. El nombre especificado detrás del operador binario de resolución de ámbito debe ser un miembro de la clase especificada a la izquierda del operador o un miembro de su clase o clases base.

Los nombres especificados detrás del operador de selección de miembro (**.** o **->**) deben ser miembros del tipo de clase del objeto especificado a la izquierda del operador o miembros de su clase o clases base. Los nombres especificados a la derecha del operador de selección de miembro (**->**) también pueden ser objetos de otro tipo de clase, siempre que el lado izquierdo de **->** es un objeto de clase y que la clase define un operador de selección de miembro sobrecargado (**->**) que se evalúa como un puntero a algún otro tipo de clase. (Esta especificación se explica con más detalle en [acceso a miembros de clase](../cpp/member-access.md).)

El compilador busca los nombres en el orden siguiente y se detiene cuando encuentra el nombre:

1. El ámbito de bloque actual si el nombre se utiliza dentro de una función; en caso contrario, el ámbito global.

1. En el exterior, a través de cada ámbito de bloque contenedor, incluido el ámbito de función más externo (que incluye parámetros de función).

1. Si el nombre se utiliza dentro de una función miembro, se busca el nombre en el ámbito de la clase.

1. El nombre se busca en las clases base de la clase.

1. Se busca en el ámbito de la clase anidada contenedora y en sus clases base. La búsqueda continúa hasta que se busque en el ámbito de la clase contenedora más externo.

1. Se busca en el ámbito global.

Sin embargo, puede modificar este orden de búsqueda de la forma siguiente:

1. Los nombres precedidos por `::` obligan a que la búsqueda se inicie en el ámbito global.

1. Los nombres precedidos por la **clase**, **struct**, y **unión** palabras clave forzar al compilador que busque sólo **clase**,  **struct**, o **unión** nombres.

1. Los nombres en el lado izquierdo del operador de resolución de ámbito (`::`) solo puede ser **clase**, **struct**, **espacio de nombres**, o **unión**nombres.

Si el nombre hace referencia a un miembro no estático pero se utiliza en una función miembro estática, se genera un mensaje de error. De forma similar, si el nombre hace referencia a cualquier miembro no estático en una clase contenedora, un mensaje de error se genera porque las clases contenidas no tienen clase contenedora **esto** punteros.

## <a name="function-parameter-names"></a>Nombres de parámetro de la función

Los nombres de los parámetros de función en las definiciones de función se consideran que están en el ámbito del bloque más externo de la función. Por consiguiente, son nombres locales y salen del ámbito cuando termina la función.

Los nombres de los parámetros de función en las declaraciones de función (prototipos) están en el ámbito local de la declaración y salen del ámbito al final de la declaración.

Los parámetros predeterminados están en el ámbito del parámetro para el que son el parámetro predeterminado, como se describe en los dos párrafos anteriores. Sin embargo, no pueden acceder a variables locales o miembros de clase no estáticos. Los parámetros predeterminados se evalúan en el punto de la llamada de función, pero se evalúan en el ámbito original de la declaración de función. Por tanto, los parámetros predeterminados de funciones miembro siempre se evalúan en el ámbito de la clase.

## <a name="see-also"></a>Vea también

[Herencia](../cpp/inheritance-cpp.md)