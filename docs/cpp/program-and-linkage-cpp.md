---
title: Programas y vinculación (C++)
ms.date: 04/09/2018
ms.assetid: a6493ba0-24e2-4c89-956e-9da1dea660cb
ms.openlocfilehash: 4f509979a293f194333e610fbdae7be9d32ec121
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62301518"
---
# <a name="program-and-linkage-c"></a>Programa y vinculación (C++)

En un programa de C++, un *símbolos*, por ejemplo un nombre de variable o función, se puede declarar cualquier número de veces dentro de su ámbito, pero solo puede definirse una vez. Se trata de la regla de una definición (ODR). Un *declaración* presenta (o volver a presenta) un nombre en el programa. Un *definición* introduce un nombre y, en el caso de una variable, explícitamente lo inicializa. Un *definición de función* consta de la firma y el cuerpo de la función.

Estas son las declaraciones:

```cpp
int i;
int f(int x);
```

Estas son las definiciones:

```cpp
int i{42};
int f(int x){ return x * i; }
```

Un programa consta de uno o varios *unidades de traducción*. Una unidad de traducción está formada por un archivo de implementación (.cpp, .cxx, etc.) y todos los encabezados (. h, .hpp, etc.) que incluyen directa o indirectamente. Cada unidad de traducción se compila de forma independiente por el compilador, después de que el vinculador combina las unidades de traducción compilada en un único *programa*. Las infracciones de la regla ODR normalmente aparecen como errores del vinculador cuando el mismo nombre tiene dos definiciones diferentes en diferentes unidades de traducción.

En general, es la mejor manera de hacer que una variable visible en varios archivos para colocarla en un archivo de encabezado y agregue un #include (directiva) en cada archivo .cpp que requiere la declaración. Agregando *#include guards* todo el contenido del encabezado, asegúrese de que los nombres declara solo se definen una vez.

Sin embargo, en algunos casos puede ser necesario declarar una variable global o clase en un archivo. cpp. En esos casos, necesita una manera de saber el compilador y vinculador si el nombre del objeto se aplica únicamente al archivo de uno o a todos los archivos.

## <a name="linkage-vs-scope"></a>Vinculación frente a ámbito

El concepto de *vinculación* hace referencia a la visibilidad de símbolos globales (por ejemplo, variables, los nombres de tipo y los nombres de función) dentro del programa como un todo a través de unidades de traducción. El concepto de *ámbito* hace referencia a los símbolos que se declaran dentro de un bloque, como un espacio de nombres, clase o el cuerpo de función. Estos símbolos solo son visibles dentro del ámbito en el que se definen; el concepto de vinculación no se aplica a ellos.

## <a name="external-vs-internal-linkage"></a>Externa frente a la vinculación interna

Un *función gratis* es una función que se define en global o ámbito de espacio de nombres. Variables globales que no son constantes y funciones libres de forma predeterminada tienen *vinculación externa*; son visibles desde cualquier unidad de traducción en el programa. Por lo tanto, ningún otro objeto global (variable, definición de clase, etc.) puede tener ese nombre. Un símbolo con *vinculación interna* o *sin vinculación* solo es visible en la unidad de traducción en el que se declara. Cuando un nombre tiene vinculación interna, el mismo nombre puede existir en otra unidad de traducción. Las variables declaradas con las definiciones de clase o los cuerpos de funciones no tienen ninguna vinculación.

Puede forzar un nombre global para tienen vinculación interna declarando explícitamente como **estático**. Esto limita su visibilidad a la misma unidad de traducción en el que se declara. Tenga en cuenta que en este contexto, **estático** significa algo distinto a cuando se aplica a las variables locales.

Los siguientes objetos tienen vinculación interna de forma predeterminada:
- objetos const
- objetos de constexpr
- typedefs
- objetos estáticos en el ámbito de espacio de nombres

Para dar una vinculación externa de objeto const, declárelo como **extern** y asignarle un valor:

```cpp
extern const int value = 42;
```

Consulte [extern](extern-cpp.md) para obtener más información.

## <a name="see-also"></a>Vea también

[Conceptos básicos](../cpp/basic-concepts-cpp.md)