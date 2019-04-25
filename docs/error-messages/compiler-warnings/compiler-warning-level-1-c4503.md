---
title: Advertencia del compilador (nivel 1) C4503
ms.date: 05/14/2018
f1_keywords:
- C4503
helpviewer_keywords:
- C4503
ms.assetid: 7c5a98ae-5b6d-41d8-b881-12d3ffd5e392
ms.openlocfilehash: 94c88511d87c3adf3cf5687a94948c83ebc5b3d5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160983"
---
# <a name="compiler-warning-level-1-c4503"></a>Advertencia del compilador (nivel 1) C4503

> '*identificador*': superada, la longitud del nombre representativo nombre aparece truncado

## <a name="remarks"></a>Comentarios

Esta advertencia del compilador está obsoleta y no se genera en Visual Studio 2017 y posterior compiladores.

El nombre representativo es mayor que el límite del compilador (4096) y se ha truncado. Para evitar esta advertencia y el truncamiento, reduzca el número de argumentos o la longitud de nombre de los identificadores utilizados. Nombres de los que ya que el límite del compilador tienen un valor hash que se aplican y no corren el riesgo de un conflicto de nombres representativos.

Cuando se usa una versión anterior de Visual Studio, esta advertencia puede emitirse cuando el código contiene plantillas especializadas en plantillas repetidamente. Por ejemplo, un mapa de mapas (de la biblioteca estándar de C++). En esta situación, puede hacer las definiciones de tipos un tipo (un **struct**, por ejemplo) que contiene el mapa.

Sin embargo, podría decidir no reestructurar el código.  Es posible distribuir una aplicación que genera la advertencia C4503, pero si se producen errores en tiempo de vínculo en un símbolo truncado, puede ser más difícil determinar el tipo del símbolo en el error. Depuración también puede ser más difícil; el depurador puede tener dificultades para asignar el nombre del símbolo en el nombre del tipo. La corrección del programa, sin embargo, se ve afectada por el nombre truncado.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C4503 en compiladores antes de Visual Studio 2017:

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

En este ejemplo se muestra una manera de volver a escribir el código para resolver la advertencia C4503:

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