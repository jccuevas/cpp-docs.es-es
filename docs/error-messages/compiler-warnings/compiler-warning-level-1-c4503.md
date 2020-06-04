---
title: Advertencia del compilador (nivel 1) C4503
ms.date: 05/14/2018
f1_keywords:
- C4503
helpviewer_keywords:
- C4503
ms.assetid: 7c5a98ae-5b6d-41d8-b881-12d3ffd5e392
ms.openlocfilehash: 9077c448f3b5f1d70d18047b91dcf300e606c91f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186554"
---
# <a name="compiler-warning-level-1-c4503"></a>Advertencia del compilador (nivel 1) C4503

> '*Identifier*': se superó la longitud del nombre representativo; el nombre se truncó

## <a name="remarks"></a>Observaciones

Esta advertencia del compilador está obsoleta y no se genera en los compiladores de Visual Studio 2017 y posteriores.

El nombre representativo era más largo que el límite del compilador (4096) y se truncó. Para evitar esta advertencia y el truncamiento, reduzca el número de argumentos o las longitudes de nombre de los identificadores utilizados. Los nombres representativos que superan el límite del compilador tienen un hash aplicado y no están en peligro de un conflicto de nombres.

Cuando se usa una versión anterior de Visual Studio, esta advertencia se puede emitir cuando el código contiene plantillas especializadas en plantillas de forma repetida. Por ejemplo, un mapa de mapas (de la C++ biblioteca estándar). En esta situación, puede convertir la typedefs en un tipo (un **struct**, por ejemplo) que contiene la asignación.

Sin embargo, es posible que decida no reestructurar el código.  Es posible enviar una aplicación que genera C4503, pero si se producen errores de tiempo de vínculo en un símbolo truncado, puede ser más difícil determinar el tipo de símbolo en el error. La depuración también puede ser más difícil. es posible que el depurador haya asignado el nombre de símbolo a un nombre de tipo. La corrección del programa, sin embargo, no se ve afectada por el nombre truncado.

## <a name="example"></a>Ejemplo

En el siguiente ejemplo se genera C4503 en compiladores antes de Visual Studio 2017:

```cpp
// C4503.cpp
// compile with: /W1 /EHsc /c
// C4503 expected
#include <string>
#include <map>

class Field{};

typedef std::map<std::string, Field> Screen;
typedef std::map<std::string, Screen> WebApp;
typedef std::map<std::string, WebApp> WebAppTest;
typedef std::map<std::string, WebAppTest> Hello;
Hello MyWAT;
```

En este ejemplo se muestra una manera de reescribir el código para resolver C4503:

```cpp
// C4503b.cpp
// compile with: /W1 /EHsc /c
#include <string>
#include <map>

class Field{};

struct Screen2 {
   std::map<std::string, Field> Element;
};

struct WebApp2 {
   std::map<std::string, Screen2> Element;
};

struct WebAppTest2 {
   std::map<std::string, WebApp2> Element;
};

struct Hello2 {
   std::map<std::string, WebAppTest2> Element;
};

Hello2 MyWAT2;
```
