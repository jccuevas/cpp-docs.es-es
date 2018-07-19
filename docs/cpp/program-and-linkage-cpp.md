---
title: Programas y vinculación (C++) | Documentos de Microsoft
ms.custom: ''
ms.date: 04/09/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: a6493ba0-24e2-4c89-956e-9da1dea660cb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2dba8698461636e292771fc1e5a4f5ac0a633e73
ms.sourcegitcommit: d06966efce25c0e66286c8047726ffe743ea6be0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36238674"
---
# <a name="program-and-linkage-c"></a>Programa y vinculación (C++)

En un programa de C++, un *símbolos*, por ejemplo un nombre de variable o función, puede declarar cualquier número de veces dentro de su ámbito, pero solo puede definirse una vez. Se trata de la regla de una definición (ODR). A *declaración* presenta (o restablezca) un nombre en el programa. A *definición* introduce un nombre y, en el caso de una variable, explícitamente lo inicializa. A *definición de función* consta de la firma y el cuerpo de la función.

Estas declaraciones son:

```cpp
int i;
int f(int x);
```

Se trata de definiciones:

```cpp
int i{42};
int f(int x){ return x * i; }
```

Un programa consta de uno o varios *unidades de traducción*. Una unidad de traducción está formada por un archivo de implementación (.cpp, .cxx, etc.) y todos los encabezados (. h, .hpp, etc.) que incluye directa o indirectamente. Cada unidad de traducción se compila de forma independiente por el compilador, y después de que el vinculador combina las unidades de traducción compilada en un único *programa*. Las infracciones de la regla ODR normalmente aparecen como errores del vinculador cuando el mismo nombre tiene dos definiciones diferentes en diferentes unidades de traducción.

En general, es la mejor manera de hacer que una variable visible a través de varios archivos para colocarla en un archivo de encabezado y agregar un #include (directiva) en cada archivo .cpp que requiere la declaración. Agregando *#include guards* alrededor del contenido de encabezado, asegúrese de que los nombres declara sólo se definen una vez.

Sin embargo, en algunos casos puede ser necesario declarar una variable global o clase en un archivo .cpp. En esos casos, necesita una manera para indicar el compilador y el vinculador si el nombre del objeto se aplica solo a un archivo o a todos los archivos.

## <a name="linkage-vs-scope"></a>Vinculación frente a ámbito

El concepto de *vinculación* hace referencia a la visibilidad de símbolos globales (por ejemplo, las variables, los nombres de tipo y los nombres de función) dentro del programa como un todo a través de unidades de traducción. El concepto de *ámbito* hace referencia a los símbolos que se declaran dentro de un bloque, como un espacio de nombres, la clase o el cuerpo de la función. Estos símbolos solo son visibles dentro del ámbito en el que se definen; el concepto de vinculación no se aplica a ellos. 

## <a name="external-vs-internal-linkage"></a>Externa frente a la vinculación interna

A *libre función* es una función que se define en global o en el ámbito de espacio de nombres. Variables globales no son constantes y funciones libres de forma predeterminada tienen *vinculación externa*; son visibles desde cualquier unidad de traducción en el programa. Por lo tanto, ningún otro objeto global (variable, definición de clase, etc.) puede tener ese nombre. Un símbolo con *vinculación interna* o *sin vinculación* solamente sea visible en la unidad de traducción en el que se declara. Cuando un nombre tiene vinculación interna, puede existir el mismo nombre en otra unidad de traducción. Las variables declaradas con las definiciones de clase o cuerpos de las funciones no tienen ninguna vinculación. 

Puede forzar que tienen vinculación interna mediante la declaración explícita como un nombre global **estático**. Esto limita su visibilidad en la misma unidad de traducción en el que se declara. Tenga en cuenta que en este contexto, **estático** significa algo distinto a cuando se aplican a las variables locales.

Los siguientes objetos tienen vinculación interna predeterminada:
- objetos constantes
- objetos de constexpr
- typedefs
- objetos estáticos en el ámbito de espacio de nombres

Para conceder a una vinculación externa de objeto const, declárelo como **extern** y asignarle un valor:

```cpp
extern const int value = 42;
```

Vea [extern](extern-cpp.md) para obtener más información.

## <a name="see-also"></a>Vea también

 [Conceptos básicos](../cpp/basic-concepts-cpp.md)