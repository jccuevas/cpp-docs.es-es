---
title: Información general de los módulos en C++
ms.date: 07/23/2019
helpviewer_keywords:
- modules [C++]
- modules [C++], overview
description: Los módulos de C++ 20 proporcionan una alternativa moderna a los archivos de encabezado.
ms.openlocfilehash: 17495aa3e295b26fcfa5c489ff6793bb75d13d68
ms.sourcegitcommit: fd0f8839da5c6a3663798a47c6b0bb6e63b518bd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2019
ms.locfileid: "70273679"
---
# <a name="overview-of-modules-in-c"></a>Información general de los módulos en C++

C++ 20 presenta *módulos*, una solución moderna para la componentización C++ de bibliotecas y programas. Un módulo es un conjunto de archivos de código fuente que se compilan de forma independiente de las [unidades de traducción](https://wikipedia.org/wiki/Translation_unit_(programming)) que los importan. Los módulos eliminan o reducen considerablemente muchos de los problemas asociados con el uso de archivos de encabezado y también pueden reducir los tiempos de compilación. Las macros, las directivas de preprocesador y los nombres no exportados declarados en un módulo no son visibles y, por lo tanto, no tienen ningún efecto en la compilación de la unidad de traducción que importa el módulo. Puede importar módulos en cualquier orden sin preocuparse por las redefiniciones de macros. Las declaraciones de la unidad de traducción de importación no participan en la resolución de sobrecarga o en la búsqueda de nombres en el módulo importado. Después de compilar un módulo una vez, los resultados se almacenan en un archivo binario que describe todos los tipos, funciones y plantillas exportados. Ese archivo se puede procesar mucho más rápido que un archivo de encabezado y el compilador puede reutilizarlo cada lugar en el que se importe el módulo en un proyecto.

Los módulos se pueden usar en paralelo con los archivos de encabezado. Un C++ archivo de origen puede importar módulos y también #include archivos de encabezado. En algunos casos, el preprocesador puede importar un archivo de encabezado como un módulo en lugar de #included textualmente. Se recomienda que los nuevos proyectos usen módulos en lugar de archivos de encabezado lo máximo posible. En el caso de los proyectos existentes de mayor tamaño en desarrollo activo, se recomienda experimentar con la conversión de encabezados heredados a módulos para ver si obtiene una reducción significativa en los tiempos de compilación.

## <a name="enable-modules-in-the-microsoft-c-compiler"></a>Habilitar módulos en el compilador de Microsoft C++

A partir de la versión 16,2 de Visual Studio 2019, los módulos no se implementan totalmente en el compilador de Microsoft C++ . Puede usar la característica módulos para crear módulos de una sola partición e importar los módulos de la biblioteca estándar que proporciona Microsoft. Para habilitar la compatibilidad con los módulos, compile con [/experimental: module](../build/reference/experimental-module.md) y [/STD: c + + latest](../build/reference/std-specify-language-standard-version.md). En un proyecto de Visual Studio, haga clic con el botón secundario en el nodo del proyecto en **Explorador de soluciones** y elija **propiedades**. Establezca la lista desplegable **configuración** en **todas las configuraciones**y, a continuación, elija **propiedades** > de configuración > **C/C++** **Language** > **enable C++ modules ( experimental)** .

Un módulo y el código que lo consume deben compilarse con las mismas opciones del compilador.

## <a name="consume-the-c-standard-library-as-modules"></a>Usar la C++ biblioteca estándar como módulos

Aunque no se especifica en el estándar C++ 20, Microsoft permite que la implementación C++ de la biblioteca estándar se importe como módulos. Al importar la C++ biblioteca estándar como módulos en lugar de #including a través de los archivos de encabezado, puede acelerar los tiempos de compilación según el tamaño del proyecto. La biblioteca se pone en componente en los siguientes módulos:

- STD. Regex proporciona el contenido del encabezado \<regex >
- STD. FileSystem proporciona el contenido del encabezado \<filesystem >
- STD. Memory proporciona el contenido de la \<memoria del encabezado >
- STD. Threading proporciona el contenido de los encabezados \<Atomic >, \<condition_variable >, \<Future > \<, mutex > \<, shared_mutex > y \<Thread >
- STD. Core proporciona todo lo demás en C++ la biblioteca estándar

Para consumir estos módulos, solo tiene que agregar una instrucción Import en la parte superior del archivo de código fuente. Por ejemplo:

```cpp
import std.core;
import std.regex;
```

Para consumir el módulo de la biblioteca estándar de Microsoft, debe compilar el programa con las opciones [/EHsc](../build/reference/eh-exception-handling-model.md) y [/MD](../build/reference/md-mt-ld-use-run-time-library.md) .

## <a name="basic-example"></a>Ejemplo básico

En el ejemplo siguiente se muestra una definición de módulo simple en un archivo de código fuente denominado **foo. IXX**. La extensión **. IXX** es necesaria para los archivos de interfaz de módulo en Visual Studio. En este ejemplo, el archivo de interfaz contiene la definición de función, así como la declaración. Sin embargo, las definiciones también se pueden colocar en uno o varios archivos independientes (como se muestra en un ejemplo posterior). La instrucción **Export Module foo** indica que este archivo es la interfaz principal para un módulo denominado `Foo`. El modificador de exportación `f()` en indica que esta función estará visible cuando `Foo` lo importe otro programa o módulo. Tenga en cuenta que el módulo hace `Bar`referencia a un espacio de nombres.

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

El archivo **Program. cpp** usa la instrucción **Import** para tener acceso al nombre que exporta `Foo`. Tenga en cuenta que `Bar` el nombre es visible aquí, pero no todos sus miembros. Tenga en cuenta también que `ANSWER` la macro no está visible.

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

## <a name="implementing-modules"></a>Implementar módulos

Puede crear un módulo con un solo archivo de interfaz (. IXX) que exporta nombres e incluye implementaciones de todos los tipos y funciones. También puede colocar las implementaciones en uno o varios archivos de implementación independientes, de forma similar a como se usan los archivos. h y. cpp. La palabra clave **Export** solo se usa en el archivo de interfaz. Un archivo de implementación puede **importar** otro módulo, pero no puede **exportar** ningún nombre. Los archivos de implementación se pueden denominar con cualquier extensión. Un archivo de interfaz y el conjunto de archivos de implementación que respaldan se tratan como una clase especial de unidad de traducción denominada *unidad de módulo*. Un nombre que se declara en cualquier archivo de implementación es visible automáticamente en todos los demás archivos de la misma unidad de módulo.

En el caso de los módulos de mayor tamaño, puede dividir el módulo en varias unidades de módulo denominadas *particiones*. Cada partición consta de un archivo de interfaz respaldado por uno o varios archivos de implementación. (A partir de la versión 16,2 de Visual Studio 2019, las particiones aún no están totalmente implementadas).

## <a name="modules-namespaces-and-argument-dependent-lookup"></a>Módulos, espacios de nombres y búsqueda dependiente de argumentos

Las reglas para los espacios de nombres en los módulos son las mismas que en cualquier otro código. Si se exporta una declaración dentro de un espacio de nombres, el espacio de nombres envolvente (excepto los miembros no exportados) también se exporta implícitamente. Si un espacio de nombres se exporta explícitamente, se exportan todas las declaraciones dentro de esa definición de espacio de nombres.

Al realizar una búsqueda dependiente de argumentos para las resoluciones de sobrecarga en la unidad de traducción de importación, el compilador tiene en cuenta las funciones que se declaran en la misma unidad de traducción (incluidas las interfaces de módulo) que el tipo de los argumentos de la función. se definen.

### <a name="module-partitions"></a>Particiones de módulos

> [!NOTE]
> Esta sección se proporciona por integridad. Las particiones aún no se han implementado C++ en el compilador de Microsoft.

Un módulo se puede dividir en *particiones*, cada uno de los cuales consta de un archivo de interfaz y cero o más archivos de implementación. Una partición de módulo es similar a un módulo, salvo que comparte la propiedad de todas las declaraciones en todo el módulo. Todos los nombres exportados por los archivos de la interfaz de partición se importan y se vuelven a exportar mediante el archivo de interfaz principal. El nombre de una partición debe comenzar con el nombre del módulo seguido de un signo de dos puntos. Las declaraciones en cualquiera de las particiones están visibles en todo el módulo. No se necesitan precauciones especiales para evitar errores de la regla de una definición (ODR). Puede declarar un nombre (función, clase, etc.) en una partición y definirlo en otro. Un archivo de implementación de partición comienza de la siguiente manera:

```cpp
module Foo:part1
```

y el archivo de interfaz de partición se inicia de la siguiente manera:

```cpp
export module Foo:part1
```

Para obtener acceso a las declaraciones de otra partición, una partición debe importarla, pero solo puede usar el nombre de la partición, no el nombre del módulo:

```cpp
module Foo:part2;
import :part1;
```

La unidad de interfaz principal debe importar y volver a exportar todos los archivos de partición de la interfaz del módulo de la siguiente manera:

```cpp
export import :part1
export import :part2
...
```

La unidad de interfaz principal puede importar archivos de implementación de particiones, pero no puede exportarlos porque no se permite que los nombres exporten ningún nombre. Esto permite a un módulo mantener los detalles de implementación internos en el módulo.

## <a name="modules-and-header-files"></a>Módulos y archivos de encabezado

Puede incluir los archivos de encabezado en un archivo de origen de módulo `#include` colocando la Directiva antes de la declaración de módulo. Estos archivos se consideran en el fragmento de *módulo global*. Un módulo solo puede ver los nombres en el *fragmento de módulo global* que se encuentran en los encabezados que incluye explícitamente. El fragmento de módulo global solo contiene los símbolos que se usan realmente.

```cpp
// MyModuleA.cpp

#include "customlib.h"
#include "anotherlib.h"

import std.core;
import MyModuleB;

//... rest of file
```

Puede usar un archivo de encabezado tradicional para controlar los módulos que se importan:

```cpp
// MyProgram.h
import std.core;
#ifdef DEBUG_LOGGING
import std.filesystem;
#endif
```

### <a name="imported-header-files"></a>Archivos de encabezado importados

> [!NOTE]
> Esta sección solo es meramente informativa. Las importaciones heredadas todavía no se han C++ implementado en el compilador de Microsoft.

Algunos encabezados son suficientemente independientes para que se les permita usar la palabra clave **Import** . La diferencia principal entre un encabezado importado y un módulo importado es que las definiciones de preprocesador del encabezado están visibles en el programa de importación inmediatamente después de la instrucción Import. (Las definiciones de preprocesador de los archivos incluidos en ese encabezado *no* son visibles).

```cpp
import <vector>
import "myheader.h"
```

## <a name="see-also"></a>Vea también

[módulo, importación y exportación](import-export-module.md)
