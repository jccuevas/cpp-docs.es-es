---
title: Unidades de traducción y vinculación (C++)
ms.date: 12/11/2019
ms.assetid: a6493ba0-24e2-4c89-956e-9da1dea660cb
ms.openlocfilehash: 791ec53d4df863b218db463f2b9b9401bf6f466d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374316"
---
# <a name="translation-units-and-linkage"></a>Unidades de traducción y vinculación

En un programa C++, un *símbolo,* por ejemplo, una variable o un nombre de función, se puede declarar cualquier número de veces dentro de su ámbito, pero solo se puede definir una vez. Esta regla es la "Regla de una definición" (ODR). Una *declaración* introduce (o reintroduce) un nombre en el programa. Una *definición* introduce un nombre. Si el nombre representa una variable, una definición la inicializa explícitamente. Una definición de *función* consta de la firma más el cuerpo de la función. Una definición de clase consta del nombre de clase seguido de un bloque que enumera todos los miembros de la clase. (Los cuerpos de las funciones miembro pueden definirse opcionalmente por separado en otro archivo.)

En el ejemplo siguiente se muestran algunas declaraciones:

```cpp
int i;
int f(int x);
class C;
```

En el ejemplo siguiente se muestran algunas definiciones:

```cpp
int i{42};
int f(int x){ return x * i; }
class C {
public:
   void DoSomething();
};
```

Un programa consta de una o más unidades de *traducción.* Una unidad de traducción consta de un archivo de implementación y todos los encabezados que incluye directa o indirectamente. Los archivos de implementación suelen tener una extensión de archivo de *cpp* o *cxx*. Los archivos de encabezado suelen tener una extensión de *h* o *hpp*. Cada unidad de traducción se compila de forma independiente por el compilador. Una vez completada la compilación, el vinculador combina las unidades de traducción compiladas en un único *programa.* Las infracciones de la regla ODR suelen aparecer como errores del vinculador. Los errores del vinculador se producen cuando el mismo nombre tiene dos definiciones diferentes en diferentes unidades de traducción.

En general, la mejor manera de hacer visible una variable en varios archivos es colocarla en un archivo de encabezado. A continuación, agregue una directiva #include en cada archivo *cpp* que requiera la declaración. Al agregar protectores de *inclusión* alrededor del contenido del encabezado, se asegura de que los nombres que declara solo se definen una vez.

En C++20, los [módulos](modules-cpp.md) se introducen como una alternativa mejorada a los archivos de encabezado.

En algunos casos puede ser necesario declarar una variable o clase global en un archivo *cpp.* En esos casos, necesita una manera de indicar al compilador y al vinculador qué tipo de *vinculación* tiene el nombre. El tipo de vinculación especifica si el nombre del objeto se aplica solo a un archivo o a todos los archivos. El concepto de vinculación se aplica únicamente a los nombres globales. El concepto de vinculación no se aplica a los nombres que se declaran dentro de un ámbito. Un ámbito se especifica mediante un conjunto de llaves envolventes, como en definiciones de función o clase.

## <a name="external-vs-internal-linkage"></a>Vinculación externa frente a interna

Una *función libre* es una función que se define en el ámbito global o de espacio de nombres. Las variables globales no const y las funciones libres de forma predeterminada tienen *vinculación externa;* son visibles desde cualquier unidad de traducción en el programa. Por lo tanto, ningún otro objeto global puede tener ese nombre. Un símbolo con *vinculación interna* o *sin vinculación* sólo es visible dentro de la unidad de traducción en la que se declara. Cuando un nombre tiene vinculación interna, el mismo nombre puede existir en otra unidad de traducción. Las variables declaradas con definiciones de clase o cuerpos de función no tienen vinculación.

Puede forzar un nombre global para que tenga vinculación interna declarándolo explícitamente como **estático.** Esto limita su visibilidad a la misma unidad de traducción en la que se declara. En este contexto, **static** significa algo diferente que cuando se aplica a variables locales.

Los siguientes objetos tienen vinculación interna de forma predeterminada:

- const objetos
- constexpr objetos
- typedefs
- objetos estáticos en el ámbito del espacio de nombres

Para dar un vínculo externo de objeto const, declárelo como **extern** y asígnele un valor:

```cpp
extern const int value = 42;
```

Consulte [extern](extern-cpp.md) para obtener más información.

## <a name="see-also"></a>Consulte también

[Conceptos básicos](../cpp/basic-concepts-cpp.md)
