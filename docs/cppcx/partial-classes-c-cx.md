---
title: Clases parciales (C++/CX)
ms.date: 12/30/2016
ms.assetid: 69d93575-636c-4564-8cca-6dfba0c7e328
ms.openlocfilehash: 71df19e98192a7704d4528fe730ce79977383a9b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385003"
---
# <a name="partial-classes-ccx"></a>Clases parciales (C++/CX)

Una clase parcial es una construcción que admite escenarios en los que estás modificando una parte de una definición de clase, y el software que genera código automático, por ejemplo el diseñador XAML, también está modificando código en la misma clase. Mediante el uso de una clase parcial, puedes evitar que el diseñador sobrescriba tu código. En un proyecto de Visual Studio, el modificador `partial` se aplica automáticamente al archivo generado.

## <a name="syntax"></a>Sintaxis

Para definir una clase parcial, utiliza la palabra clave `partial` inmediatamente delante de la "clase-clave" de lo que de otro modo sería una definición de clase normal. Una palabra clave como `partial ref class` es una palabra clave contextual que contiene caracteres de espacio en blanco. Las definiciones parciales se admiten en las siguientes construcciones.

- `class` o `struct`

- `ref class` o `ref struct`

- `value class` o `value struct`

- `enum` o `enum class`

- `ref interface`, `interface class`, `interface struct`o `__interface`

- `union`

En este ejemplo se muestra una `ref class`parcial:

[!code-cpp[cx_partial#01](../cppcx/codesnippet/CPP/partialclassexample/class1.h#01)]

## <a name="contents"></a>Contenido

Una definición de clase parcial puede contener cualquier elemento que la definición de clase completa puede contener si la palabra clave `partial` se ha omitido. Con una excepción, esto incluye cualquier construcción válida como clases base, miembros de datos, funciones de miembro, enumeraciones, declaraciones de confianza y atributos. Y se permiten definiciones en línea de miembros de datos estáticos.

La excepción es la accesibilidad de clase. Por ejemplo, la instrucción `public partial class MyInvalidClass {/* ... */};` es un error. Los especificadores de acceso que se utilizan en una definición de clase parcial para MyInvalidClass no afectan a la accesibilidad predeterminada en una definición de clase completa o clase parcial subsiguiente para MyInvalidClass.

En el fragmento de código siguiente se muestra la accesibilidad. En la primera clase parcial, `Method1` es público porque su accesibilidad es pública. En la segunda clase parcial, `Method2` es privado porque la accesibilidad de clase predeterminada es privada.

[!code-cpp[cx_partial#02](../cppcx/codesnippet/CPP/partialclassexample/class1.h#02)]

## <a name="declaration"></a>Declaración

Una definición parcial de una clase como *MyClass* es solo una declaración de MyClass. Es decir, solo introduce el nombre *MyClass*. *MyClass* no se puede usar de forma que sea necesaria una definición de clase, por ejemplo, conocer el tamaño de *MyClass* o usar una base o un miembro de *MyClass*. Se considera que*MyClass* solo está definido cuando el compilador encuentra una definición no parcial de *MyClass*.

En el ejemplo siguiente se muestra el comportamiento de declaración de una clase parcial. Después de Declaration #1, *MyClass* se puede usar como si estuviera escrita como declaración adelantada, `ref class MyClass;`. Declaration #2 es equivalente a Declaration #1.Declaration #3 es válida porque es una declaración adelantada a una clase. Pero Declaration #4 no es válida porque

*MyClass* no está totalmente definida.

Declaration #5 no usa la palabra clave `partial` y la declaración define totalmente *MyClass*. Por consiguiente, Declaration #6 es válida.

[!code-cpp[Cx_partial#03](../cppcx/codesnippet/CPP/partialclassexample/class1.h#03)]

## <a name="number-and-ordering"></a>Número y orden

Puede que haya cero o más definiciones de clase parcial para cada definición completa de una clase.

Cada definición de clase parcial de una clase debe preceder léxicamente a la definición completa de esa clase, pero no tiene que preceder a las declaraciones adelantadas de la clase. Si no hay ninguna definición completa de la clase, las declaraciones de clase parcial solo pueden ser declaraciones adelantadas.

Todas las "clase-claves" como `class` y `struct` deben coincidir. Por ejemplo, el código siguiente es erróneo: `partial class X {}; struct X {};`.

En el ejemplo siguiente se muestra el número y el orden. La última declaración parcial produce un error porque la clase ya está definida.

[!code-cpp[cx_partial#04](../cppcx/codesnippet/CPP/partialclassexample/class1.h#04)]

## <a name="full-definition"></a>Definición completa

En el punto de la definición completa de la clase X, el comportamiento es el mismo que si la definición de X hubiera declarado todas las clases base, miembros, etc., en el orden en que se encontraron y se definieron en las clases parciales. Es decir, el contenido de las clases parciales se trata como si estuviera escrito en el punto de definición completa de la clase, y la búsqueda de nombre y otras reglas de lenguaje se aplican en el punto de la definición completa de la clase como si el contenido de las clases parciales se hubiera escrito en contexto

Los dos ejemplos de código siguientes tienen idénticos significado y efecto. En el primer ejemplo se utiliza una clase parcial y en el segundo ejemplo no.

[!code-cpp[cx_partial#05](../cppcx/codesnippet/CPP/partialclassexample/class1.h#05)]

[!code-cpp[cx_partial#06](../cppcx/codesnippet/CPP/partialclassexample/class1.h#06)]

## <a name="templates"></a>Plantillas

Una clase parcial no puede ser una plantilla.

## <a name="restrictions"></a>Restricciones

Una clase parcial no puede abarcar más allá de una unidad de traducción.

La palabra clave `partial` solo se admite en combinación con la palabra clave `ref class` o la palabra clave `value class` .

### <a name="examples"></a>Ejemplos

En el ejemplo siguiente se define la clase `Address` en dos archivos de código. El diseñador modifica `Address.details.h` y tú modificas `Address.h`. Solo la definición de clase del primer archivo utiliza la palabra clave `partial` .

[!code-cpp[cx_partial#07](../cppcx/codesnippet/CPP/partialclassexample/address.details.h#07)]

[!code-cpp[cx_partial#09](../cppcx/codesnippet/CPP/partialclassexample/address.h#09)]

## <a name="see-also"></a>Vea también

[Sistema de tipos](../cppcx/type-system-c-cx.md)<br/>
[Referencia del lenguaje de Visual C++](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Referencia de espacios de nombres](../cppcx/namespaces-reference-c-cx.md)
