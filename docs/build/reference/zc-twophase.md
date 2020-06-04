---
title: /Zc:twoPhase- (Deshabilitar la búsqueda de nombres en dos fases)
description: 'Explica cómo/ZC: twoPhase: deshabilita la búsqueda de nombres en dos fases cuando se especifica/permissive-.'
ms.date: 12/03/2019
f1_keywords:
- twoPhase
- /Zc:twoPhase
helpviewer_keywords:
- twoPhase
- disable two-phase name lookup
- /Zc:twoPhase
ms.openlocfilehash: 3464759793a2dd243024a9f3f52263f76514033a
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438644"
---
# <a name="zctwophase--disable-two-phase-name-lookup"></a>/Zc:twoPhase- (Deshabilitar la búsqueda de nombres en dos fases)

La opción **/Zc: twoPhase-** , en **/permissive-** , indica al compilador que use el comportamiento del compilador de C++ Microsoft original y no conforme para analizar y crear instancias de plantillas de clase y plantillas de función.

## <a name="syntax"></a>Sintaxis

> **/ZC: twoPhase-**

## <a name="remarks"></a>Observaciones

Visual Studio 2017 versión 15,3 y versiones posteriores: en [/permissive-](permissive-standards-conformance.md), el compilador usa la búsqueda de nombres en dos fases para la resolución de nombres de plantilla. Si también especifica **/Zc: twoPhase-** , el compilador vuelve a su anterior plantilla de clase no conforme y a la resolución de nombres y comportamiento de sustitución. Cuando no se especifica **/permissive-** , el comportamiento no conforme es el valor predeterminado.

Los archivos de encabezado de Windows SDK de la versión 10.0.15063.0 (Creators Update o RS2) y versiones anteriores no funcionan en modo de cumplimiento. Se requiere **/Zc: twoPhase-** para compilar el código de esas versiones del SDK cuando se usa **/permissive-** . Las versiones de la Windows SDK a partir de la versión 10.0.15254.0 (Fall Creators Update o RS3) funcionan correctamente en el modo de cumplimiento. No requieren la opción **/Zc: twoPhase-** .

Use **/Zc: twoPhase:** si el código requiere que el comportamiento anterior se compile correctamente. Considere la posibilidad de actualizar el código para que se ajuste a la norma.

### <a name="compiler-behavior-under-zctwophase-"></a>Comportamiento del compilador en/ZC: twoPhase-

De forma predeterminada, o en la versión 15,3 de Visual Studio 2017 y versiones posteriores, cuando se especifican tanto **/permissive-** como **/Zc: twoPhase**, el compilador usa este comportamiento:

- Analiza solo la declaración de plantilla, el encabezado de clase y la lista de clases base. El cuerpo de la plantilla se captura como un flujo de tokens. No se analiza ningún cuerpo de función, inicializadores, argumentos predeterminados ni argumentos noexception. Se crea una instancia de la plantilla de clase en un tipo provisional para validar que las declaraciones de la plantilla de clase son correctas. Considere esta plantilla de clase:

   ```cpp
   template <typename T> class Derived : public Base<T> { ... }
   ```

   Se analiza la declaración de plantilla, `template <typename T>`, el `class Derived`de encabezado de clase y el `public Base<T>` de lista de clase base, pero el cuerpo de la plantilla se captura como un flujo de tokens.

- Al analizar una plantilla de función, el compilador solo analiza la firma de la función. El cuerpo de la función nunca se analiza. En su lugar, se captura como un flujo de tokens.

Como resultado, si el cuerpo de la plantilla tiene errores de sintaxis, pero la plantilla nunca obtiene una instancia, el compilador no diagnostica los errores.

Otro efecto de este comportamiento es la resolución de sobrecarga. El comportamiento no estándar se produce debido al modo en que la secuencia de token se expande en el sitio de la creación de instancias. Los símbolos que no estaban visibles en la declaración de plantilla pueden estar visibles en el momento de la creación de instancias. Esto significa que pueden participar en la resolución de sobrecarga. Puede que las plantillas cambien el comportamiento en función del código que no estuviera visible en la definición de la plantilla, contrariamente al estándar.

Por ejemplo, considere este código:

```cpp
// zctwophase.cpp
// To test options, compile by using
// cl /EHsc /nologo /W4 zctwophase.cpp
// cl /EHsc /nologo /W4 /permissive- zctwophase.cpp
// cl /EHsc /nologo /W4 /permissive- /Zc:twoPhase- zctwophase.cpp

#include <cstdio>

void func(long) { std::puts("Standard two-phase") ;}

template<typename T> void g(T x)
{
    func(0);
}

void func(int) { std::puts("Microsoft one-phase"); }

int main()
{
    g(6174);
}
```

Este es el resultado cuando se usa el modo predeterminado, el modo de cumplimiento y el modo de cumplimiento con las opciones **/Zc: twoPhase-** Compiler:

```cmd
C:\Temp>cl /EHsc /nologo /W4 zctwophase.cpp && zctwophase
zctwophase.cpp
Microsoft one-phase

C:\Temp>cl /EHsc /nologo /W4 /permissive- zctwophase.cpp && zctwophase
zctwophase.cpp
Standard two-phase

C:\Temp>cl /EHsc /nologo /W4 /permissive- /Zc:twoPhase- zctwophase.cpp && zctwophase
zctwophase.cpp
Microsoft one-phase
```

Cuando se compila en modo de cumplimiento en **/permissive-** , este programa imprime "`Standard two-phase`", ya que la segunda sobrecarga de `func` no está visible cuando el compilador alcanza la plantilla. Si agrega **/Zc: twoPhase-** , el programa imprime "`Microsoft one-phase`". La salida es la misma que cuando no se especifica **/permissive-** .

*Los nombres dependientes* son nombres que dependen de un parámetro de plantilla. Estos nombres tienen un comportamiento de búsqueda que también es diferente en **/Zc: twoPhase-** . En el modo de cumplimiento, los nombres dependientes no están enlazados en el punto de la definición de la plantilla. En su lugar, el compilador los busca cuando crea una instancia de la plantilla. En el caso de las llamadas de función con un nombre de función dependiente, el nombre se enlaza a las funciones visibles en el sitio de llamada en la definición de plantilla. Se agregan sobrecargas adicionales de la búsqueda dependiente de argumentos, en el punto de la definición de plantilla y en el punto de creación de instancias de la plantilla.

La búsqueda en dos fases consta de dos partes: la búsqueda de nombres no dependientes durante la definición de la plantilla y la búsqueda de nombres dependientes durante la creación de instancias de la plantilla. En **/Zc: twoPhase-** , el compilador no realiza la búsqueda dependiente de argumentos por separado de la búsqueda no completa. Es decir, no realiza búsquedas en dos fases, por lo que los resultados de la resolución de sobrecarga pueden ser diferentes.

Este es otro ejemplo:

```cpp
// zctwophase1.cpp
// To test options, compile by using
// cl /EHsc /W4 zctwophase1.cpp
// cl /EHsc /W4 /permissive- zctwophase1.cpp
// cl /EHsc /W4 /permissive- /Zc:twoPhase- zctwophase1.cpp

#include <cstdio>

void func(long) { std::puts("func(long)"); }

template <typename T> void tfunc(T t) {
    func(t);
}

void func(int) { std::puts("func(int)"); }

namespace NS {
    struct S {};
    void func(S) { std::puts("NS::func(NS::S)"); }
}

int main() {
    tfunc(1729);
    NS::S s;
    tfunc(s);
}
```

Cuando se compila sin **/permissive-** , este código imprime:

```Output
func(int)
NS::func(NS::S)
```

Cuando se compila con **/permissive-** , pero sin **/Zc: twoPhase**, este código imprime:

```Output
func(long)
NS::func(NS::S)
```

Cuando se compila con **/permissive-** y **/Zc: twoPhase**, este código imprime:

```Output
func(int)
NS::func(NS::S)
```

En el modo de cumplimiento, en **/permissive-** , la llamada `tfunc(1729)` se resuelve en la sobrecarga de `void func(long)`. No se resuelve en la `void func(int)` sobrecarga, como en **/Zc: twoPhase-** . Esto se debe a que el `func(int)` sin calificar se declara después de la definición de la plantilla y no se encuentra a través de la búsqueda dependiente de argumentos. Pero `void func(S)` participa en la búsqueda dependiente de argumentos, por lo que se agrega al conjunto de sobrecargas para el `tfunc(s)`de llamada, aunque se declare después de la función de plantilla.

### <a name="update-your-code-for-two-phase-conformance"></a>Actualización del código para la conformidad en dos fases

Las versiones anteriores del compilador no requieren las palabras clave `template` y C++ `typename` siempre que las requiera el estándar. Estas palabras clave son necesarias en algunas posiciones para eliminar la ambigüedad sobre cómo los compiladores deben analizar un nombre dependiente durante la primera fase de la búsqueda. Por ejemplo:

`T::Foo<a || b>(c);`

Un compilador conforme analiza `Foo` como una variable en el ámbito de `T`, lo que significa que este código es una expresión or lógica con `T::foo < a` como operando izquierdo y `b > (c)` como operando derecho. Si quiere usar `Foo` como una plantilla de función, debe indicar que se trata de una plantilla agregando la palabra clave `template`:

`T::template Foo<a || b>(c);`

En las versiones de Visual Studio 2017 versión 15,3 y posteriores, cuando se especifican **/permissive-** y **/Zc: twoPhase** , el compilador permite este código sin la palabra clave `template`. Interpreta el código como una llamada a una plantilla de función con un argumento de `a || b`, porque solo analiza las plantillas de manera limitada. El código anterior no se analiza en la primera fase. Durante la segunda fase, hay suficiente contexto para indicar que `T::Foo` es una plantilla en lugar de una variable, por lo que el compilador no exige el uso de la palabra clave.

Este comportamiento también se puede consultar si se elimina la palabra clave `typename` antes de los nombres de los cuerpos de la plantilla de función, los inicializadores, los argumentos predeterminados y los argumentos noexception. Por ejemplo:

```cpp
template<typename T>
typename T::TYPE func(typename T::TYPE*)
{
    /* typename */ T::TYPE i;
}
```

Si no usa la palabra clave `typename` en el cuerpo de la función, este código se compila en **/permissive-/ZC: twoPhase-** , pero no solo en **/permissive-** . La palabra clave `typename` es necesaria para indicar que el `TYPE` depende de. Dado que el cuerpo no se analiza en **/Zc: twoPhase-** , el compilador solicitado no requiere la palabra clave. En el modo de cumplimiento de **/permissive-** , el código sin la palabra clave `typename` genera errores. Para migrar el código a la conformidad en la versión 15,3 de Visual Studio 2017 y versiones posteriores, inserte la palabra clave `typename` donde falta.

Del mismo modo, tenga en cuenta este ejemplo de código:

```cpp
template<typename T>
typename T::template X<T>::TYPE func(typename T::TYPE)
{
    typename T::/* template */ X<T>::TYPE i;
}
```

En **/permissive-/ZC: twoPhase-** y en los compiladores anteriores, el compilador solo requiere la palabra clave `template` en la línea 2. En el modo de cumplimiento, el compilador ahora también requiere la palabra clave `template` en la línea 4 para indicar que `T::X<T>` es una plantilla. Busque código al que le falta esta palabra clave y proporcione el código conforme a la norma.

Para obtener más información sobre los problemas de cumplimiento, vea [ C++ mejoras de conformidad en Visual Studio](../../overview/cpp-conformance-improvements.md) y [comportamiento no estándar](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Seleccione la página de propiedades **Propiedades de configuración** > **C/C++**  > **Línea de comandos**.

1. Modifique la propiedad **opciones adicionales** para incluir **/Zc: twoPhase-** y, a continuación, elija **Aceptar**.

## <a name="see-also"></a>Consulte también

[/Zc (Ajuste)](zc-conformance.md)
