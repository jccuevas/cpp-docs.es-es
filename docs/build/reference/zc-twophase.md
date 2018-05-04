---
title: /Zc:twoPhase-(búsqueda de nombre en dos fases de disable) | Documentos de Microsoft
ms.custom: ''
ms.date: 03/06/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- twoPhase
- /Zc:twoPhase
- VC.Project.VCCLCompilerTool.EnforceTypeConversionRules
dev_langs:
- C++
helpviewer_keywords:
- twoPhase
- disable two-phase name lookup
- /Zc:twoPhase
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5653959b25105f10ae98768217524dc0ff0cbe2a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="zctwophase--disable-two-phase-name-lookup"></a>/Zc:twoPhase-(búsqueda de nombre en dos fases de disable)

Cuando el **/Zc:twoPhase-** se especifica la opción, el compilador analiza y crea instancias de plantillas de clase y las plantillas de función de la misma manera que en versiones de Visual Studio anteriores a Visual Studio 2017 versión 15.3 no conformes. 

## <a name="syntax"></a>Sintaxis

> **/Zc:twoPhase-**

## <a name="remarks"></a>Comentarios

En Visual Studio 2017 versión 15,3 y versiones posteriores, de forma predeterminada, el compilador utiliza la búsqueda de nombre en dos fases para la resolución de nombre de plantilla. Si **/Zc:twoPhase-** se especifica, el compilador vuelve a su anterior no conformes función y plantilla plantilla nombre resolución y sustitución de comportamiento de la clase.

El **/Zc:twoPhase-** no se establece la opción para habilitar el comportamiento que no cumple las especificaciones de forma predeterminada. El [/ permisivo-](permissive-standards-conformance.md) opción establece implícitamente el comportamiento del compilador que cumplan con búsqueda en dos fases, pero se puede invalidar usando **/Zc:twoPhase-**.

Los archivos de encabezado de Windows SDK en la versión 10.0.15063.0 (creadores de actualización o Redstone 2) y versiones anteriores no funcionan correctamente en el modo de ajuste. Debe usar **/Zc:twoPhase-** para compilar código para esas versiones SDK cuando se usan la versión de Visual Studio de 2017 15.3 y versiones posteriores. Versiones del SDK de Windows a partir de la versión 10.0.15254.0 (3 Redstone o actualización de creadores de otoño) funcione correctamente en el modo de cumplimiento y no requieren la **/Zc:twoPhase-** opción.

Use **/Zc:twoPhase-** si el código requiere el comportamiento anterior para compilarse correctamente. Considerar la posibilidad de actualizar el código para que se ajuste a la norma.

### <a name="compiler-behavior-under-zctwophase-"></a>Comportamiento del compilador en /Zc:twoPhase-

En las versiones del compilador antes de Visual Studio 2017 versión 15.3 y cuándo **/Zc:twoPhase-** se especifica, el compilador usa este comportamiento:

- Analiza la declaración de plantilla, el encabezado de clase y la lista de clases base. El cuerpo de la plantilla se captura como una secuencia de símbolos. Cuerpos de función, inicializadores, argumentos predeterminados o argumentos de noexcept no se ha analizado. La plantilla de clase es pseudo crea una instancia de un tipo provisional para validar que las declaraciones de la plantilla de clase son correctas. Tenga en cuenta esta plantilla de clase:

   ```cpp
   template <typename T> class Derived : public Base<T> { ... }
   ```

   La declaración de plantilla, `template <typename T`>, el encabezado de la clase `class Derived`y la lista de clases base `public Base<T>` se analizan, pero el cuerpo de la plantilla se captura como una secuencia de símbolos.

- Al analizar una plantilla de función, el compilador analiza la firma de la función. Nunca se analiza el cuerpo de la función. En su lugar, se capturan como una secuencia de símbolos.

Como resultado, si el cuerpo de plantilla tiene errores de sintaxis y nunca se crea una instancia de la plantilla, nunca se diagnosticar los errores.

Otro efecto de este comportamiento está en la resolución de sobrecarga. Debido al modo en que el flujo de tokens se expande en el sitio de la creación de instancias, símbolos que no eran visibles en la declaración de plantilla pueden estar visible en el momento de creación de instancias y participar en la resolución de sobrecarga. Esto puede conducir a plantillas que cambian el comportamiento que se basa en código que no estaba visible cuando se definió la plantilla, al contrario que en el estándar.

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

Cuando se compila en **/Zc:twoPhase-**, este programa imprime "la llamada resuelve a int". En el modo de cumplimiento en **/ permisivo-**, este programa imprime "la llamada resuelve a void *", porque la segunda sobrecarga de `func` no está visible cuando el compilador encuentra la plantilla.

*Nombres dependientes*, nombres que dependen de un parámetro de plantilla, tienen un comportamiento de búsqueda que también es diferente en **/Zc:twoPhase-**. En el modo de cumplimiento, los nombres dependientes no se enlazan en el momento de la definición de la plantilla. En su lugar, estos nombres se buscan cuando se crea una instancia de la plantilla. Para las llamadas de función con un nombre de función dependiente, el nombre se enlaza al conjunto de funciones que están visibles en el momento de la llamada en la definición de la plantilla, como anteriormente. Las sobrecargas adicionales de búsqueda dependiente de argumentos se agregan en el punto de la definición de plantilla y el punto de donde se crea una instancia de la plantilla. Las dos fases de búsqueda en dos fases son la búsqueda de nombres no dependientes en el momento de la definición de la plantilla y la búsqueda de nombres dependientes en el momento de creación de instancias de plantilla. En **/Zc:twoPhase-**, el compilador no lleva a cabo búsqueda dependiente de argumentos por separado de búsqueda normal y no completo (es decir, no una búsqueda en dos fases), por lo que los resultados de la resolución de sobrecarga pueden ser diferentes.

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

En el modo de cumplimiento en **/ permisivo-**, la llamada `tfunc(1729)` se resuelve como el `void func(long)` sobrecarga, no `void func(int)` sobrecarga en **/Zc:twoPhase-**, ya que el no calificado `func(int)` se declara después de la definición de la plantilla y no se encuentran a través de la búsqueda dependiente de argumentos. Pero `void func(S)` participar en la búsqueda dependiente de argumentos, por lo que se agrega a la sobrecarga establecido para la llamada `tfunc(s)` incluso si se declara después de la función de plantilla.

### <a name="update-your-code-for-two-phase-conformance"></a>Actualice el código para comprobar su conformidad en dos fases

Las versiones anteriores del compilador no requieren las palabras clave `template` y `typename` en cualquier lugar en que se requiere el estándar de C++. Estas palabras clave se necesitan en algunas posiciones para eliminar la ambigüedad de cómo los compiladores deben analizar un nombre dependiente durante la primera fase de la búsqueda. Por ejemplo:

`T::Foo<a || b>(c);`

Analiza un compilador que cumplan con `Foo` como una variable en el ámbito de `T`, lo que significa que este código es un valor lógico- o una expresión con `T::foo < a` como el operando izquierdo y `b > (c)` como el operando derecho. Si quiere utilizar `Foo` como una plantilla de función, debe indicar que esto sea una plantilla mediante la adición de la `template` palabra clave:

`T::template Foo<a || b>(c);`

En versiones anteriores a Visual Studio 2017 versión 15.3 y cuándo **/Zc:twoPhase-** se especifica, el compilador permite este código sin el `template` palabra clave y lo interpreta como una llamada a una plantilla de función con un argumento de `a || b`, ya que analiza las plantillas de forma muy limitada. El código anterior no analiza en absoluto en la primera fase. Durante la segunda fase hay suficiente contexto para indicar que `T::Foo` es una plantilla en lugar de una variable por lo que el compilador no exige el uso de la palabra clave.

Este comportamiento también puede verse mediante la eliminación de la palabra clave `typename` antes de nombres en los cuerpos de plantilla de función, inicializadores, argumentos predeterminados y noexcept argumentos. Por ejemplo:

```cpp
template<typename T>
typename T::TYPE func(typename T::TYPE*)
{
    /* typename */ T::TYPE i;
}
```

Si no utiliza la palabra clave `typename` en el cuerpo de la función, este código se compila en **/Zc:twoPhase-**, pero no en **/ permisivo-**. El `typename` palabra clave es necesaria para indicar que el `TYPE` es dependiente. Dado que no se analiza el cuerpo en **/Zc:twoPhase-**, el compilador does't requieren la palabra clave. En **/ permisivo-** el modo de cumplimiento, código sin el `typename` palabra clave genera errores. Para migrar el código en Visual Studio 2017 versión 15.3 y más allá, inserte el `typename` palabra clave que está presente.

De forma similar, tenga en cuenta este ejemplo de código:

```cpp
template<typename T>
typename T::template X<T>::TYPE func(typename T::TYPE)
{
    typename T::/* template */ X<T>::TYPE i;
}
```

En **/Zc:twoPhase-** y en los compiladores anteriores, el compilador requiere sólo el `template` palabra clave en la línea 2. De forma predeterminada y en el modo de cumplimiento, el compilador ahora también requiere la `template` palabra clave en línea 4 para indicar que `T::X<T>` es una plantilla. Buscar código que le falta esta palabra clave y suministrarlo para hacer que el código se ajusta al estándar.

Para obtener más información acerca de los problemas de conformidad, vea [mejoras de conformidad de C++ en Visual Studio](../../cpp-conformance-improvements-2017.md) y [comportamiento no estándar](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **C/C++** > **línea de comandos** página de propiedades.

1. Modificar el **opciones adicionales** propiedad para incluir **/Zc:twoPhase-** y, a continuación, elija **Aceptar**.

## <a name="see-also"></a>Vea también

[/Zc (Ajuste)](../../build/reference/zc-conformance.md)<br/>
