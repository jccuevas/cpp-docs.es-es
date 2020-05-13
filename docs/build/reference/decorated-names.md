---
title: Nombres representativos
ms.date: 09/05/2018
helpviewer_keywords:
- decorated names, definition
- name decoration [C++]
- names [C++], decorated
ms.assetid: a4e9ae8e-b239-4454-b401-4102793cb344
ms.openlocfilehash: f6d81029d20d9aaca96ff184f48e94a9ce35d56e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320501"
---
# <a name="decorated-names"></a>Nombres representativos

Las funciones, los datos y los objetos de los programas C y C++ se representan internamente con sus nombres representativos. Un *nombre representativo* es una cadena codificada creada por el compilador durante la compilación de un objeto, datos o definición de función. Registra las convenciones de llamada, los tipos, los parámetros de función y otra información junto con el nombre. Esta decoración de nombre, también conocida como *mangling*de nombres, ayuda al vinculador a encontrar las funciones y objetos correctos al vincular un ejecutable.

Las convenciones de nomenclatura decoradas han cambiado en varias versiones de Visual Studio y también pueden ser diferentes en diferentes arquitecturas de destino. Para vincular correctamente con los archivos de origen creados mediante Visual Studio, C y C++ DLL y bibliotecas deben compilarse mediante el mismo conjunto de herramientas del compilador, marcas y arquitectura de destino.

> [!NOTE]
> Las bibliotecas creadas con Visual Studio 2015 pueden ser consumidas por aplicaciones creadas con Visual Studio 2017 o Visual Studio 2019.

## <a name="using-decorated-names"></a><a name="Using"></a>Uso de nombres decorados

Normalmente, no es necesario saber el nombre representativo para escribir código que se compile y se vincule correctamente. Los nombres representativos son un detalle de implementación interno del compilador y el enlazador. En general, las herramientas tratan el nombre en su formato no representativo. Sin embargo, a veces es necesario un nombre representativo cuando se especifica un nombre de función para el enlazador y otras herramientas. Por ejemplo, para que coincida con funciones de C++ sobrecargadas, miembros de espacios de nombres, constructores de clase, destructores y funciones de miembro especiales, se debe especificar el nombre representativo. Para obtener más información sobre las marcas de opción y otras situaciones que necesitan nombres representativos, vea la documentación de las herramientas y opciones que esté usando.

Si cambia el nombre de la función, la clase, la convención de llamada, el tipo de valor devuelto o cualquier otro parámetro, también cambia el nombre representativo. En este caso, debe obtener el nuevo nombre representativo y usarlo en lugar del nombre anterior en todos los lugares en los que se haya especificado.

La decoración de nombres también es importante cuando se vincula a código escrito en otros lenguajes de programación o con otros compiladores. Diferentes compiladores usan convenciones de decoración de nombres distintas. Cuando se vincula una aplicación ejecutable con el código escrito en otro idioma, se debe tener especial cuidado para que los nombres importados y exportados y las convenciones de llamada coincidan. El código de lenguaje ensamblador debe usar los nombres decorados por MSVC y las convenciones de llamada para vincular al código fuente escrito con MSVC.

## <a name="format-of-a-c-decorated-name"></a><a name="Format"></a>Formato de un nombre decorado C++

El nombre representativo para una función de C++ contiene la información siguiente:

- Nombre de función.

- Clase de la que la función es miembro, si se trata de una función miembro. Esto puede incluir la clase que contiene la clase que contiene la función y así sucesivamente.

- Espacio de nombres al que pertenece la función, si forma parte de un espacio de nombres.

- Tipos de los parámetros de las funciones.

- Convención de llamada.

- Tipo de valor devuelto de la función.

Los nombres de función y de clase están codificados en el nombre representativo. El resto del nombre representativo es un código que tiene significado interno solo para el compilador y el enlazador. Aquí tiene algunos ejemplos de nombres de C++ representativo y no representativo.

|Nombre no representativo|Nombre representativo|
|----------------------|--------------------|
|`int a(char){int i=3;return i;};`|`?a@@YAHD@Z`|
|`void __stdcall b::c(float){};`|`?c@b@@AAGXM@Z`|

## <a name="format-of-a-c-decorated-name"></a><a name="FormatC"></a>Formato de un nombre decorado en C

El formato de decoración para una función de C depende de la convención de llamada usada en su declaración, tal como se muestra en la tabla siguiente. Este también es el formato de decoración que se usa cuando el código de C++ se declara para que contenga vinculación de `extern "C"`. La convención de llamada predeterminada es `__cdecl`. Tenga en cuenta que en un entorno de 64 bits, las funciones no se decoran.

|Convención de llamada|Decoración|
|------------------------|----------------|
|`__cdecl`|Subrayado inicial (**_**)|
|`__stdcall`|Subrayado inicial (**_**) y**\@** un signo final ( ) seguido del número de bytes en la lista de parámetros en decimal|
|`__fastcall`|Señales iniciales y**\@** finales ( ) seguidas de un número decimal que representa el número de bytes en la lista de parámetros|
|`__vectorcall`|Dos signos finales (**\@**) seguidos de un número decimal de bytes en la lista de parámetros|

## <a name="viewing-decorated-names"></a><a name="Viewing"></a>Visualización de nombres decorados

Puede obtener el formato representativo del nombre de un símbolo después de compilar el archivo de origen que contiene el prototipo o la definición de la función, los datos o el objeto. Para examinar los nombres representativos del programa, puede usar uno de los métodos siguientes:

#### <a name="to-use-a-listing-to-view-decorated-names"></a>Para usar una lista para ver nombres representativos

1. Genere una lista compilando el archivo de origen que contiene la definición o prototipo de datos, objeto o función con la opción del compilador Tipo de archivo de [listado](fa-fa-listing-file.md) establecida en Ensamblado con código fuente (**/FAs**).

   Por ejemplo, `cl /c /FAs example.cpp` escriba en un símbolo del sistema para desarrolladores para generar un archivo de lista, example.asm.

2. En el archivo de lista resultante, busque la línea que empieza por PUBLIC y termina con un punto y coma seguido del nombre no representativo de la función o los datos. El símbolo situado entre PUBLIC y el punto y coma es el nombre representativo.

#### <a name="to-use-dumpbin-to-view-decorated-names"></a>Para usar DUMPBIN para ver nombres representativos

1. Para ver los símbolos exportados en un `dumpbin /symbols` `objfile` archivo .obj o .lib, escriba en un símbolo del sistema para desarrolladores.

2. Para encontrar el formato representativo de un símbolo, busque el nombre no representativo entre paréntesis. El nombre representativo está en la misma línea, después de un carácter de tubería (&#124;) y antes del nombre no decorado.

## <a name="viewing-undecorated-names"></a><a name="Undecorated"></a>Visualización de nombres no decorados

Puede usar undname.exe para convertir un nombre representativo a su formato no representativo. En este ejemplo se muestra cómo funciona:

```
C:\>undname ?func1@a@@AAEXH@Z
Microsoft (R) C++ Name Undecorator
Copyright (C) Microsoft Corporation. All rights reserved.

Undecoration of :- "?func1@a@@AAEXH@Z"
is :- "private: void __thiscall a::func1(int)"
```

## <a name="see-also"></a>Consulte también

[Herramientas de compilación de MSVC adicionales](c-cpp-build-tools.md)<br/>
[Usar extern para especificar la vinculación](../../cpp/using-extern-to-specify-linkage.md)
