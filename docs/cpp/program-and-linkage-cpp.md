---
title: Unidades de traducción y vinculación (C++)
ms.date: 12/11/2019
ms.assetid: a6493ba0-24e2-4c89-956e-9da1dea660cb
ms.openlocfilehash: dcd66b454da3758996fe827581fe4a73a641407f
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301358"
---
# <a name="translation-units-and-linkage"></a>Unidades de traducción y vinculación

En un C++ programa, un *símbolo*, por ejemplo un nombre de variable o función, se puede declarar cualquier número de veces dentro de su ámbito, pero solo se puede definir una vez. Esta regla es la "regla de definición única" (ODR). Una *declaración* introduce (o vuelve a introducir) un nombre en el programa. Una *definición* introduce un nombre. Si el nombre representa una variable, una definición la inicializa explícitamente. Una *definición de función* se compone de la firma más el cuerpo de la función. Una definición de clase consta del nombre de clase seguido de un bloque que enumera todos los miembros de clase. (Los cuerpos de las funciones miembro se pueden definir opcionalmente de forma independiente en otro archivo).

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

Un programa consta de una o varias *unidades de traducción*. Una unidad de traducción se compone de un archivo de implementación y de todos los encabezados que incluye directa o indirectamente. Normalmente, los archivos de implementación tienen una extensión de archivo de *CPP* o *CXX*. Los archivos de encabezado suelen tener una extensión de *h* o *HPP*. El compilador compila cada unidad de traducción de forma independiente. Una vez completada la compilación, el vinculador combina las unidades de traducción compiladas en un único *programa*. Las infracciones de la regla ODR suelen aparecer como errores del vinculador. Los errores del enlazador se producen cuando el mismo nombre tiene dos definiciones diferentes en unidades de traducción diferentes.

En general, la mejor manera de hacer que una variable sea visible en varios archivos es colocarla en un archivo de encabezado. A continuación, agregue una directiva de #include en cada archivo *CPP* que requiera la declaración. Al agregar las *protecciones include* en torno al contenido del encabezado, se asegura de que los nombres que declara se definen solo una vez.

En C++ 20, los [módulos](modules-cpp.md) se presentan como una alternativa mejorada a los archivos de encabezado.

En algunos casos, puede ser necesario declarar una variable global o una clase en un archivo *CPP* . En esos casos, necesita una manera de indicar al compilador y vinculador qué tipo de *vinculación* tiene el nombre. El tipo de vinculación especifica si el nombre del objeto se aplica solo al archivo o a todos los archivos. El concepto de vinculación solo se aplica a los nombres globales. El concepto de vinculación no se aplica a los nombres que se declaran dentro de un ámbito. Un ámbito se especifica mediante un conjunto de llaves de inclusión, como en las definiciones de función o de clase.

## <a name="external-vs-internal-linkage"></a>Vinculación externa frente a interna

Una *función gratuita* es una función que se define en un ámbito global o de espacio de nombres. De forma predeterminada, las variables globales no const y las funciones libres tienen *vinculación externa*. están visibles desde cualquier unidad de traducción del programa. Por lo tanto, ningún otro objeto global puede tener ese nombre. Un símbolo con *vinculación interna* o *sin vinculación* solo es visible dentro de la unidad de traducción en la que se declara. Cuando un nombre tiene vinculación interna, puede existir el mismo nombre en otra unidad de traducción. Las variables declaradas con definiciones de clase o cuerpos de función no tienen vinculación.

Puede forzar que un nombre global tenga vinculación interna si lo declara explícitamente como **estático**. Esto limita su visibilidad a la misma unidad de traducción en la que se declara. En este contexto, **static** significa algo diferente de cuando se aplica a variables locales.

Los objetos siguientes tienen vinculación interna de forma predeterminada:
- const (objetos)
- objetos constexpr
- typedefs
- objetos estáticos en el ámbito de espacio de nombres

Para proporcionar una vinculación externa a un objeto const, declárelo como **extern** y asígnele un valor:

```cpp
extern const int value = 42;
```

Consulte [extern](extern-cpp.md) para obtener más información.

## <a name="see-also"></a>Vea también

[Conceptos básicos](../cpp/basic-concepts-cpp.md)