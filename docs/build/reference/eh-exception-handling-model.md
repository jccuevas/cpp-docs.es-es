---
title: /EH (Modelo de control de excepciones)
description: Guía de referencia para las opciones del compilador de Microsoft C++ /EH (modelo de control de excepciones) en Visual Studio.
ms.date: 04/14/2020
f1_keywords:
- VC.Project.VCCLWCECompilerTool.ExceptionHandling
- /eh
- VC.Project.VCCLCompilerTool.ExceptionHandling
helpviewer_keywords:
- exception handling, compiler model
- cl.exe compiler, exception handling
- EH compiler option [C++]
- -EH compiler option [C++]
- /EH compiler option [C++]
no-loc:
- SEH
- try
- catch
- throw
- extern
- finally
- noexcept
ms.assetid: 754b916f-d206-4472-b55a-b6f1b0f2cb4d
ms.openlocfilehash: 68d6af657e7c20c0f5e84674dd91803beb35fba0
ms.sourcegitcommit: 0e4feb35b47c507947262d00349d4a893863a6d3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/15/2020
ms.locfileid: "81396295"
---
# <a name="eh-exception-handling-model"></a>/EH (Modelo de control de excepciones)

Especifica la compatibilidad del modelo de control de excepciones generada por el compilador. Los argumentos especifican `catch(...)` si se debe aplicar sintaxis a excepciones C++ throw estándar y estructuradas, **noexcept** si ** extern ** se supone que el código "C" a las excepciones y si se optimizan determinadas comprobaciones.

## <a name="syntax"></a>Sintaxis

> **`/EHa`**[**`-`**]\
> **`/EHs`**[**`-`**]\
> **`/EHc`**[**`-`**]\
> **`/EHr`**[**`-`**]

## <a name="arguments"></a>Argumentos

**`a`**\
Habilita el desenredado de pila C++ estándar. Captura las excepciones estructuradas (asincrónicas) y estándar de `catch(...)` C++ (sincrónica) cuando se utiliza la sintaxis. **`/EHa`** anula tanto **`/EHs`** **`/EHc`** los argumentos como los argumentos.

**`s`**\
Habilita el desenredado de pila C++ estándar. Captura solo excepciones estándar de C++ cuando se utiliza `catch(...)` la sintaxis. A **`/EHc`** menos que también se especifique, el compilador supone throw que las funciones declaradas como ** extern "C"** pueden ser una excepción C++.

**`c`**\
Cuando se **`/EHs`** usa con , el compilador asume throw que las funciones declaradas como ** extern "C"** nunca una excepción C++. No tiene ningún efecto **`/EHa`** cuando se **`/EHca`** utiliza **`/EHa`** con (es decir, es equivalente a ). **`/EHc`** se omite **`/EHs`** **`/EHa`** si se especifica o no.

**`r`**\
Indica al compilador que siempre genere comprobaciones de terminación en tiempo de ejecución para todas las **noexcept** funciones. De forma predeterminada, **noexcept** las comprobaciones en tiempo de ejecución se pueden optimizar si el compilador determina que la función solo llama a funciones que no son de lanzamiento. Esta opción proporciona una estricta conformidad con C++ a costa de algún código adicional. **`/EHr`** se omite **`/EHs`** **`/EHa`** si se especifica o no.

**`-`**\
Borra el argumento de opción anterior. Por ejemplo, **`/EHsc-`** se **`/EHs /EHc-`** interpreta como , **`/EHs`** y es equivalente a .

**`/EH`** los argumentos pueden especificarse por separado o combinados, en cualquier orden. Si se especifica más de una instancia del mismo argumento, la última invalida las anteriores.  Por **`/EHr- /EHc /EHs`** ejemplo, es **`/EHscr-`** el **`/EHscr- /EHr`** mismo que , **`/EHscr`** y tiene el mismo efecto que .

## <a name="remarks"></a>Observaciones

### <a name="default-exception-handling-behavior"></a>Comportamiento de control de excepciones predeterminado

El compilador siempre genera código queSEHadmite el control de excepciones estructurado asincrónico ( ). De forma predeterminada (es **`/EHsc`** **`/EHs`** decir, **`/EHa`** si no se especifica SEH ninguna opción , , `catch(...)` , el compilador admite controladores en la cláusula c++ nativa. Sin embargo, también genera código que solo admite parcialmente excepciones C++. El código de desenredado de excepción [try](../../cpp/try-throw-and-catch-statements-cpp.md) predeterminado no destruye los objetos C++ automáticos fuera de los bloques que salen del ámbito debido a una excepción. Las pérdidas de recursos y el comportamiento indefinido pueden producirse cuando se produce una excepción de C++.

### <a name="standard-c-exception-handling"></a>Manejo de excepciones Estándar C++

Compatibilidad completa del compilador para el modelo de control de **`/EHsc`** excepciones **`/EHs`** Estándar **`/EHa`** C++ que desenreda de forma segura los objetos de pila requiere (recomendado), o .

Si usa **`/EHs`** **`/EHsc`** o , `catch(...)` las cláusulas catch no son excepciones estructuradas asincrónicas. Cualquier infracción <xref:System.Exception?displayProperty=fullName> de acceso y excepciones administradas no se detectará. Además, los objetos en el ámbito cuando se produce una excepción asincrónica no se destruyen, incluso si el código controla la excepción asincrónica. Este comportamiento es un argumento para dejar las excepciones estructuradas sin controlar. En su lugar, considere que estas excepciones son fatales.

Cuando se **`/EHs`** **`/EHsc`** usa o , el compilador asume que **throw** las excepciones solo pueden producirse en una instrucción o en una llamada de función. Esta suposición permite al compilador eliminar el código para realizar el seguimiento de la duración de muchos objetos desenredados, lo que puede reducir significativamente el tamaño del código. Si usa **`/EHa`**, la imagen ejecutable puede ser más grande y **try** más lenta, porque el compilador no optimiza los bloques de forma tan agresiva. También deja en filtros de excepción que limpian automáticamente los objetos throw locales, incluso si el compilador no ve ningún código que pueda una excepción de C++.

### <a name="structured-and-standard-c-exception-handling"></a>Manejo estructurado y estándar de excepciones C++

La **`/EHa`** opción del compilador permite el desenredado seguro de la pila para las excepciones asincrónicas y las excepciones De C++. Admite el control de excepciones estándar de C++ y `catch(...)` estructuradas mediante la cláusula C++ nativa. Para SEH implementar sin **`/EHa`** especificar , puede utilizar la sintaxis **__try**, **__except**y **__finally.** Para obtener más información, vea [Control estructurado de excepciones](../../cpp/structured-exception-handling-c-cpp.md).

> [!IMPORTANT]
> Especificar **`/EHa`** e intentar controlar todas las `catch(...)` excepciones mediante el uso puede ser peligroso. En la mayoría de los casos, las excepciones asincrónicas son irrecuperables y podrían considerarse fatales. La detección y continuidad de estas excepciones puede dañar el proceso y generar errores que son difíciles de encontrar y corregir.
>
> Aunque Windows y Visual C++ admiten SEH, se recomienda encarecidamente que**`/EHsc`** **`/EHs`** utilice el control de excepciones C++ estándar ISO ( o ). Hace que su código sea más portátil y flexible. Todavía puede haber ocasiones SEH que tenga que usar en código heredado o para determinados tipos de programas. Es necesario en el código compilado para admitir Common Language Runtime ([/clr](clr-common-language-runtime-compilation.md)), por ejemplo. Para obtener más información, vea [Control estructurado de excepciones](../../cpp/structured-exception-handling-c-cpp.md).
>
> Se recomienda nunca vincular archivos **`/EHa`** de objeto compilados **`/EHs`** **`/EHsc`** mediante a los compilados mediante o en el mismo módulo ejecutable. Si tiene que controlar una **`/EHa`** excepción asincrónica mediante **`/EHa`** el uso de cualquier parte del módulo, utilice para compilar todo el código del módulo. Puede usar la sintaxis de control de excepciones estructurada **`/EHs`** en el mismo módulo que el código compilado mediante . Sin embargo, no SEH puede mezclar la **try** **throw** sintaxis **catch** con C++ , , y en la misma función.

Utilícelo **`/EHa`** si desea catch una excepción que se genera **throw** por algo distinto de un archivo . En este ejemplo se genera y se detecta una excepción estructurada:

```cpp
// compiler_options_EHA.cpp
// compile with: /EHa
#include <iostream>
#include <excpt.h>
using namespace std;

void fail()
{
    // generates SE and attempts to catch it using catch(...)
    try
    {
        int i = 0, j = 1;
        j /= i;   // This will throw a SE (divide by zero).
        printf("%d", j);
    }
    catch(...)
    {
        // catch block will only be executed under /EHa
        cout << "Caught an exception in catch(...)." << endl;
    }
}

int main()
{
    __try
    {
        fail();
    }

    // __except will only catch an exception here
    __except(EXCEPTION_EXECUTE_HANDLER)
    {
        // if the exception was not caught by the catch(...) inside fail()
        cout << "An exception was caught in __except." << endl;
    }
}
```

### <a name="exception-handling-under-clr"></a>Control de excepciones en /clr

La **`/clr`** opción **`/EHa`** implica (es decir, **`/clr /EHa`** es redundante). El compilador genera **`/EHs`** un **`/EHsc`** error **`/clr`** si se utiliza o se utiliza después de . Las optimizaciones no afectan a este comportamiento. Cuando se detecta una excepción, el compilador invoca los destructores de clase para los objetos que están en el mismo ámbito que la excepción. Si no se detecta una excepción, esos destructores no se ejecutan.

Para obtener información acerca **`/clr`** de las restricciones de control de excepciones en , vea [_set_se_translator](../../c-runtime-library/reference/set-se-translator.md).

### <a name="runtime-exception-checks"></a>Comprobaciones de excepciones en tiempo de ejecución

La **`/EHr`** opción fuerza las comprobaciones de **noexcept** terminación en tiempo de ejecución en todas las funciones que tienen un atributo. De forma predeterminada, las comprobaciones en tiempo de ejecución se pueden optimizar si el back-end del compilador determina que una función solo llama a funciones *que no son de lanzamiento.* Dichas funciones se componen de cualquier función que tiene un atributo que especifica que no se puede producir ninguna excepción. Incluyen funciones **noexcept** `throw()`marcadas , `__declspec(nothrow)` **`/EHc`** , y, cuando se especifica, ** extern funciones "C".** Las funciones que no producen excepciones también incluyen aquellas funciones que el compilador ha determinado que no producen excepciones durante la inspección. Puede establecer explícitamente el comportamiento **`/EHr-`** predeterminado mediante .

Un atributo no producente no es una garantía de que una función no pueda producir excepciones. A diferencia del **noexcept** comportamiento de una función, el compilador MSVC `throw()` `__declspec(nothrow)`considera una excepción iniciada por una función declarada mediante , , o ** extern "C"** como un comportamiento indefinido. Las funciones que usan estos tres atributos de declaración no aplican comprobaciones de terminación en tiempo de ejecución para las excepciones. Puede usar **`/EHr`** la opción para ayudarle a identificar este comportamiento indefinido, forzando al compilador a **noexcept** generar comprobaciones en tiempo de ejecución para las excepciones no controladas que escapen una función.

## <a name="set-the-option-in-visual-studio-or-programmatically"></a>Establezca la opción en Visual Studio o mediante programación

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener detalles, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Seleccione **Propiedades** > de configuración**C/C++** > **Generación**de código .

1. Modifique la propiedad **Habilitar excepciones de C++** .

   O bien, establezca **Habilitar excepciones de C++** en **No**y, en la página de propiedades **Línea de comandos** , en el cuadro **Opciones adicionales** , agregue la opción del compilador.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ExceptionHandling%2A>.

## <a name="see-also"></a>Consulte también

[Opciones del compilador MSVC](compiler-options.md)\
[Sintaxis de línea de comandos del compilador MSVC](compiler-command-line-syntax.md)\
[Errores y manejo de excepciones](../../cpp/errors-and-exception-handling-modern-cpp.md)\
[Especificacionesthrowde excepción ( )](../../cpp/exception-specifications-throw-cpp.md)\
[Control de excepciones estructurado (C/C++)](../../cpp/structured-exception-handling-c-cpp.md)
