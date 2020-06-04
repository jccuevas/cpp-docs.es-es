---
title: Información general de los módulos en C++
ms.date: 12/13/2019
helpviewer_keywords:
- modules [C++]
- modules [C++], overview
description: Los módulos de C++20 proporcionan una alternativa moderna a los archivos de encabezado.
ms.openlocfilehash: cd45be1dee888c8caeb65b7ff002ac8fee1ecbe1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370756"
---
# <a name="overview-of-modules-in-c"></a>Información general de los módulos en C++

C++20 presenta *módulos,* una solución moderna para la componenteización de bibliotecas y programas C++. Un módulo es un conjunto de archivos de código fuente que se compilan independientemente de las [unidades](https://wikipedia.org/wiki/Translation_unit_(programming)) de traducción que los importan. Los módulos eliminan o reducen en gran medida muchos de los problemas asociados con el uso de archivos de encabezado, y también reducen potencialmente los tiempos de compilación. Las macros, las directivas de preprocesador y los nombres no exportados declarados en un módulo no son visibles y, por lo tanto, no tienen ningún efecto en la compilación de la unidad de traducción que importa el módulo. Puede importar módulos en cualquier orden sin preocuparse por las redefiniciones de macros. Las declaraciones de la unidad de traducción de importación no participan en la resolución de sobrecargas ni en la búsqueda de nombres en el módulo importado. Después de compilar un módulo una vez, los resultados se almacenan en un archivo binario que describe todos los tipos, funciones y plantillas exportados. Ese archivo se puede procesar mucho más rápido que un archivo de encabezado y el compilador puede reutilizarlo en cada lugar donde se importe el módulo en un proyecto.

Los módulos se pueden utilizar uno al lado del otro con los archivos de encabezado. Un archivo de origen C++ puede importar módulos y también #include archivos de encabezado. En algunos casos, un archivo de encabezado se puede importar como un módulo en lugar de textualmente #included por el preprocesador. Recomendamos que los nuevos proyectos usen módulos en lugar de archivos de encabezado tanto como sea posible. Para proyectos existentes más grandes en desarrollo activo, le sugerimos que experimente con la conversión de encabezados heredados en módulos para ver si obtiene una reducción significativa en los tiempos de compilación.

## <a name="enable-modules-in-the-microsoft-c-compiler"></a>Habilitar módulos en el compilador de Microsoft C++

A partir de Visual Studio 2019 versión 16.2, los módulos no se implementan completamente en el compilador de Microsoft C++. Puede utilizar la característica de módulos para crear módulos de partición única e importar los módulos de biblioteca estándar proporcionados por Microsoft. Para habilitar la compatibilidad con módulos, compile con [/experimental:module](../build/reference/experimental-module.md) y [/std:c++latest](../build/reference/std-specify-language-standard-version.md). En un proyecto de Visual Studio, haga clic con el botón secundario en el nodo del proyecto en el **Explorador** de soluciones y elija **Propiedades**. Establezca el menú desplegable **Configuración** en **Todas las configuraciones**y, a continuación, elija Propiedades > de **configuración****C/C++** > **Language** > **Enable C++ Modules (experimental)**.

Un módulo y el código que lo consume deben compilarse con las mismas opciones del compilador.

## <a name="consume-the-c-standard-library-as-modules"></a>Consumir la biblioteca estándar C++ como módulos

Aunque no se especifica mediante el estándar C++20, Microsoft permite importar su implementación de la biblioteca estándar C++ como módulos. Al importar la biblioteca estándar C++ como módulos en lugar de #including a través de archivos de encabezado, puede acelerar potencialmente los tiempos de compilación en función del tamaño del proyecto. La biblioteca se divide en los siguientes módulos:

- std.regex proporciona el \<contenido del encabezado regex>
- std.filesystem proporciona el \<contenido del sistema de archivos de encabezado>
- std.memory proporciona el \<contenido de la memoria de encabezado>
- std.threading proporciona el contenido \<de \<los encabezados> atómicos, condition_variable>, \<> \<futuro,> de exclusión mutua, \<> de shared_mutex y \<> de subprocesos
- std.core proporciona todo lo demás en la Biblioteca Estándar C++

Para consumir estos módulos, simplemente agregue una declaración de importación a la parte superior del archivo de código fuente. Por ejemplo:

```cpp
import std.core;
import std.regex;
```

Para consumir el módulo Biblioteca estándar de Microsoft, compile el programa con las opciones [/EHsc](../build/reference/eh-exception-handling-model.md) y [/MD.](../build/reference/md-mt-ld-use-run-time-library.md)

## <a name="basic-example"></a>Ejemplo básico

En el ejemplo siguiente se muestra una definición de módulo simple en un archivo de origen denominado **Foo.ixx**. La extensión **.ixx** es necesaria para los archivos de interfaz de módulo en Visual Studio. En este ejemplo, el archivo de interfaz contiene la definición de función, así como la declaración. Sin embargo, las definiciones también se pueden colocar en uno o varios archivos independientes (como se muestra en un ejemplo posterior). La instrucción **Foo del módulo** de exportación indica `Foo`que este archivo es la interfaz principal para un módulo llamado . El modificador `f()` **de exportación** activado indica `Foo` que esta función será visible cuando se importe por otro programa o módulo. Tenga en cuenta que `Bar`el módulo hace referencia a un espacio de nombres .

```cpp
export module Foo;

#define ANSWER 42

namespace Bar
{
   int f_internal() {
        return ANSWER;
      }

   export int f() {
      return f_internal();
   }
}
```

El archivo **MyProgram.cpp** utiliza la declaración de `Foo` **importación** para tener acceso al nombre exportado por . Tenga en `Bar` cuenta que el nombre es visible aquí, pero no todos sus miembros. Tenga en cuenta `ANSWER` también que la macro no está visible.

```cpp

import Foo;
import std.core;

using namespace std;

int main()
{
   cout << "The result of f() is " << Bar::f() << endl; // 42
   // int i = Bar::f_internal(); // C2039
   // int j = ANSWER; //C2065
}

```

La declaración de importación solo puede aparecer en el ámbito global.

## <a name="implementing-modules"></a>Implementación de módulos

Puede crear un módulo con un único archivo de interfaz (.ixx) que exporte nombres e incluya implementaciones de todas las funciones y tipos. También puede colocar las implementaciones en uno o varios archivos de implementación independientes, de forma similar a cómo se utilizan los archivos .h y .cpp. La palabra clave **export** solo se utiliza en el archivo de interfaz. Un archivo de implementación puede **importar** otro módulo, pero no puede **exportar** ningún nombre. Los archivos de implementación se pueden nombrar con cualquier extensión. Un archivo de interfaz y el conjunto de archivos de implementación que lo respaldan se tratan como un tipo especial de unidad de traducción llamada unidad de *módulo.* Un nombre que se declara en cualquier archivo de implementación es visible automáticamente en todos los demás archivos dentro de la misma unidad de módulo.

Para módulos más grandes, puede dividir el módulo en varias unidades de módulo *llamadas particiones.* Cada partición consta de un archivo de interfaz respaldado por uno o más archivos de implementación. (A partir de Visual Studio 2019 versión 16.2, las particiones aún no están completamente implementadas.)

## <a name="modules-namespaces-and-argument-dependent-lookup"></a>Módulos, espacios de nombres y búsqueda dependiente de argumentos

Las reglas para espacios de nombres en módulos son las mismas que en cualquier otro código. Si se exporta una declaración dentro de un espacio de nombres, el espacio de nombres envolvente (excluyendo los miembros no exportados) también se exporta implícitamente. Si un espacio de nombres se exporta explícitamente, se exportan todas las declaraciones dentro de esa definición de espacio de nombres.

Al realizar la búsqueda dependiente de argumentos para las resoluciones de sobrecarga en la unidad de traducción de importación, el compilador considera las funciones que se declaran en la misma unidad de traducción (incluidas las interfaces de módulo) como donde se definen el tipo de argumentos de la función.

### <a name="module-partitions"></a>Particiones de módulo

> [!NOTE]
> Esta sección se proporciona para su integridad. Las particiones aún no se implementan en el compilador de Microsoft C++.

Un módulo se puede dividir en *particiones,* cada una de las dos consta de un archivo de interfaz y cero o más archivos de implementación. Una partición de módulo es similar a un módulo, excepto que comparte la propiedad de todas las declaraciones de todo el módulo. Todos los nombres exportados por archivos de interfaz de partición se importan y se vuelven a exportar mediante el archivo de interfaz principal. El nombre de una partición debe comenzar con el nombre del módulo seguido de dos puntos. Las declaraciones en cualquiera de las particiones son visibles en todo el módulo. No se necesitan precauciones especiales para evitar errores de una regla de definición (ODR). Puede declarar un nombre (función, clase, etc.) en una partición y definirlo en otra. Un archivo de implementación de partición comienza así:

```cpp
module Foo:part1
```

y el archivo de interfaz de partición comienza así:

```cpp
export module Foo:part1
```

Para acceder a las declaraciones en otra partición, una partición debe importarla, pero solo puede utilizar el nombre de la partición, no el nombre del módulo:

```cpp
module Foo:part2;
import :part1;
```

La unidad de interfaz principal debe importar y reexportar todos los archivos de partición de interfaz del módulo de la siguiente manera:

```cpp
export import :part1
export import :part2
...
```

La unidad de interfaz principal puede importar archivos de implementación de partición, pero no puede exportarlos porque esos archivos no pueden exportar ningún nombre. Esto permite que un módulo mantenga los detalles de implementación internos al módulo.

## <a name="modules-and-header-files"></a>Módulos y archivos de encabezado

Puede incluir archivos de encabezado en un `#include` archivo de origen de módulo colocando la directiva antes de la declaración de módulo. Estos archivos se consideran en el fragmento de *módulo global.* Un módulo solo puede ver los nombres en el fragmento de *módulo global* que se encuentran en encabezados que incluye explícitamente. El fragmento de módulo global solo contiene símbolos que se utilizan realmente.

```cpp
// MyModuleA.cpp

#include "customlib.h"
#include "anotherlib.h"

import std.core;
import MyModuleB;

//... rest of file
```

Puede utilizar un archivo de encabezado tradicional para controlar qué módulos se importan:

```cpp
// MyProgram.h
import std.core;
#ifdef DEBUG_LOGGING
import std.filesystem;
#endif
```

### <a name="imported-header-files"></a>Archivos de encabezado importados

> [!NOTE]
> Esta sección es sólo informativa. Las importaciones heredadas aún no se implementan en el compilador de Microsoft C++.

Algunos encabezados son lo suficientemente autónomos como para que se les permita entrar mediante la palabra clave **import.** La principal diferencia entre un encabezado importado y un módulo importado es que las definiciones de preprocesador en el encabezado son visibles en el programa de importación inmediatamente después de la instrucción de importación. (Las definiciones de preprocesador en los archivos incluidos por ese encabezado *no* son visibles.)

```cpp
import <vector>
import "myheader.h"
```

## <a name="see-also"></a>Consulte también

[módulo, importar, exportar](import-export-module.md)
