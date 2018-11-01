---
title: /Zc:twoPhase-(deshabilitar la búsqueda de nombres en dos fases)
ms.date: 03/06/2018
f1_keywords:
- twoPhase
- /Zc:twoPhase
- VC.Project.VCCLCompilerTool.EnforceTypeConversionRules
helpviewer_keywords:
- twoPhase
- disable two-phase name lookup
- /Zc:twoPhase
ms.openlocfilehash: d5a53db5a5c0ae9c4cfec76e57f628499c8955c4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50648767"
---
# <a name="zctwophase--disable-two-phase-name-lookup"></a>/Zc:twoPhase-(deshabilitar la búsqueda de nombres en dos fases)

Cuando el **/Zc:twoPhase-** se especifica la opción, el compilador analiza y crea instancias de plantillas de clase y las plantillas de función de la misma manera que las versiones de Visual Studio anteriores a Visual Studio 2017 versión 15.3 no conforme.

## <a name="syntax"></a>Sintaxis

> **/Zc:twoPhase-**

## <a name="remarks"></a>Comentarios

En Visual Studio 2017 versión 15.3 y versiones posteriores, de forma predeterminada, el compilador usa la búsqueda de nombres en dos fases para la resolución de plantilla. Si **/Zc:twoPhase-** se especifica, el compilador vuelve a su anterior clase plantilla y la función de plantilla nombre resolución y la sustitución de un comportamiento no conforme.

El **/Zc:twoPhase-** opción para habilitar un comportamiento no conforme no se establece de forma predeterminada. El [/ permissive-](permissive-standards-conformance.md) opción establece el comportamiento del compilador de búsqueda en dos fases que cumplen las especificaciones de forma implícita, pero se pueden invalidar utilizando **/Zc:twoPhase-**.

Los archivos de encabezado SDK de Windows en la versión 10.0.15063.0 (Creators Update o piedra rojiza 2) y versiones anteriores no funcionan correctamente en modo de conformidad. Debe usar **/Zc:twoPhase-** para compilar código para esas versiones del SDK cuando se usan Visual Studio 2017 versión 15.3 y versiones posteriores. Versiones del SDK de Windows empezando por la versión 10.0.15254.0 (3 de piedra rojiza o Fall Creators Update) funcione correctamente en modo de conformidad y no requieren la **/Zc:twoPhase-** opción.

Use **/Zc:twoPhase-** si el código requiere el comportamiento anterior para compilarse correctamente. Considerar la posibilidad de actualizar el código para ajustarse al estándar.

### <a name="compiler-behavior-under-zctwophase-"></a>Comportamiento del compilador en /Zc:twoPhase-

En las versiones del compilador antes de Visual Studio 2017 versión 15.3 y cuándo **/Zc:twoPhase-** se especifica, el compilador usa este comportamiento:

- Analiza solo la declaración de plantilla, el encabezado de la clase y la lista de clases base. El cuerpo de la plantilla se captura como una secuencia de símbolos. Los cuerpos de función, inicializadores, argumentos predeterminados o noexcept argumentos no se analizan. La plantilla de clase es pseudo crea una instancia de un tipo provisional para validar que las declaraciones de la plantilla de clase son correctas. Tenga en cuenta esta plantilla de clase:

   ```cpp
   template <typename T> class Derived : public Base<T> { ... }
   ```

   La declaración de plantilla, `template <typename T`>, el encabezado de la clase `class Derived`y la lista de clase base `public Base<T>` se analizan, pero el cuerpo de la plantilla se captura como una secuencia de símbolos.

- Al analizar una plantilla de función, el compilador analiza la firma de la función. Nunca se analiza el cuerpo de la función. En su lugar, se captura como una secuencia de símbolos.

Como resultado, si el cuerpo de la plantilla tiene errores de sintaxis y nunca se crea una instancia de la plantilla, nunca se diagnostican los errores.

Otro efecto de este comportamiento está en la resolución de sobrecarga. Debido al modo en que se expande la secuencia de símbolos en el sitio de la creación de instancias, los símbolos que no eran visibles en la declaración de plantilla pueden estar visible en el momento de creación de instancias y participar en la resolución de sobrecarga. Esto puede conducir a las plantillas que cambian el comportamiento basado en código que no estaba visible cuando se ha definido la plantilla, al contrario que en el estándar.

Por ejemplo, considere este código:

```cpp
#include <cstdio>

void func(void*) { std::puts("The call resolves to void*") ;}

template<typename T> void g(T x)
{
    func(0);
}

void func(int) { std::puts("The call resolves to int"); }

int main()
{
    g(3.14);
}
```

Al compilar con **/Zc:twoPhase-**, este programa imprime "la llamada se resuelve en int". En el modo de conformidad en **/ permissive-**, este programa imprime "se resuelve como la llamada a void *", porque la segunda sobrecarga de `func` no está visible cuando el compilador encuentra la plantilla.

*Los nombres dependientes*, los nombres que dependen de un parámetro de plantilla, tienen el comportamiento de búsqueda que también es diferente en **/Zc:twoPhase-**. En el modo de conformidad, los nombres dependientes no están enlazados en el punto de definición de la plantilla. En su lugar, estos nombres se buscan cuando se crea una instancia de la plantilla. Para las llamadas de función con un nombre de función dependientes, el nombre se enlaza al conjunto de funciones que están visibles en el momento de la llamada en la definición de la plantilla, que anteriormente. Las sobrecargas adicionales de la búsqueda dependiente de argumentos se agregan en el punto de la definición de plantilla y el punto de donde se crea una instancia de la plantilla. Las dos fases de búsqueda en dos fases son la búsqueda de nombres no dependientes en el momento de la definición de plantilla y la búsqueda de nombres dependientes en el momento de crear instancias de plantillas. En **/Zc:twoPhase-**, el compilador no lleva a cabo búsqueda dependiente de argumentos por separado de búsqueda normal y no completo (es decir, no hace una búsqueda en dos fases), por lo que los resultados de la resolución de sobrecarga pueden ser diferentes.

Este es otro ejemplo:

```cpp
// zctwophase1.cpp
// Compile by using
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

Cuando se compila sin **/Zc:twoPhase-**, esto imprime

```Output
func(long)
NS::func(NS::S)
```

Cuando se compila con **/Zc:twoPhase-**, esto imprime

```Output
func(int)
NS::func(NS::S)
```

En el modo de conformidad en **/ permissive-**, la llamada `tfunc(1729)` se resuelve como el `void func(long)` sobrecarga, no `void func(int)` sobrecarga como en **/Zc:twoPhase-**, ya que el incompleto `func(int)` se declara después de la definición de la plantilla y no se encuentran a través de la búsqueda dependiente de argumentos. Pero `void func(S)` participar en la búsqueda dependiente de argumentos, por lo que se agrega a la sobrecarga que establecer para llamar `tfunc(s)` , aunque se declara después de la función de plantilla.

### <a name="update-your-code-for-two-phase-conformance"></a>Actualice el código para comprobar su conformidad en dos fases

Las versiones anteriores del compilador no requieren las palabras clave `template` y `typename` en cualquier lugar en que se requiere el estándar de C++. Estas palabras clave se necesitan en algunas posiciones para eliminar la ambigüedad de cómo los compiladores deben analizar un nombre dependiente durante la primera fase de búsqueda. Por ejemplo:

`T::Foo<a || b>(c);`

Analiza un compilador adecuado `Foo` como una variable en el ámbito de `T`, lo que significa que este código es un valor lógico: o expresión con `T::foo < a` como el operando izquierdo y `b > (c)` como el operando derecho. Si quería utilizar `Foo` como una plantilla de función, debe indicar que esto es una plantilla mediante la adición de la `template` palabra clave:

`T::template Foo<a || b>(c);`

En las versiones anteriores de Visual Studio 2017 versión 15.3 y cuándo **/Zc:twoPhase-** se especifica, el compilador permite este código sin el `template` palabra clave y lo interpreta como una llamada a una plantilla de función con un argumento de `a || b`, ya que analiza las plantillas en un modo muy limitado. No se puede analizar en todo el código anterior en la primera fase. Durante la segunda fase no hay suficiente contexto para indicar que `T::Foo` es una plantilla en lugar de una variable de modo que el compilador no exige el uso de la palabra clave.

Este comportamiento también se puede ver mediante la eliminación de la palabra clave `typename` antes de los nombres de los cuerpos de plantilla de función, los inicializadores, argumentos predeterminados y noexcept argumentos. Por ejemplo:

```cpp
template<typename T>
typename T::TYPE func(typename T::TYPE*)
{
    /* typename */ T::TYPE i;
}
```

Si no usa la palabra clave `typename` en el cuerpo de función, este código se compila en **/Zc:twoPhase-**, pero no en **/ permissive-**. El `typename` palabra clave es necesaria para indicar que el `TYPE` es dependiente. Dado que no se analiza el cuerpo en **/Zc:twoPhase-**, el compilador does't requieren la palabra clave. En **/ permissive-** modo de conformidad, el código sin el `typename` palabra clave genera errores. Para migrar el código a Visual Studio 2017 versión 15.3 y posteriores, inserte el `typename` palabra clave donde está presente.

De forma similar, considere este ejemplo de código:

```cpp
template<typename T>
typename T::template X<T>::TYPE func(typename T::TYPE)
{
    typename T::/* template */ X<T>::TYPE i;
}
```

En **/Zc:twoPhase-** y en compiladores antiguos, el compilador sólo requiere la `template` palabra clave en la línea 2. De forma predeterminada y en modo de conformidad, el compilador ahora también requiere la `template` palabra clave en la línea 4 para indicar que `T::X<T>` es una plantilla. Buscar código que le falta la palabra clave this y proporcionarlo para que el código se ajusta al estándar.

Para obtener más información acerca de problemas de conformidad, consulte [mejoras de conformidad de C++ en Visual Studio](../../cpp-conformance-improvements-2017.md) y [comportamiento no estándar](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **C o C++** > **línea de comandos** página de propiedades.

1. Modificar el **opciones adicionales** propiedad incluir **/Zc:twoPhase-** y, a continuación, elija **Aceptar**.

## <a name="see-also"></a>Vea también

[/Zc (Ajuste)](../../build/reference/zc-conformance.md)<br/>
