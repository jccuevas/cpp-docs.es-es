---
title: /EH (Modelo de control de excepciones)
ms.date: 08/14/2018
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
ms.assetid: 754b916f-d206-4472-b55a-b6f1b0f2cb4d
ms.openlocfilehash: 8546b14995317afb57e4cc23a5d6f81c2172a1a6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328291"
---
# <a name="eh-exception-handling-model"></a>/EH (Modelo de control de excepciones)

Especifica el tipo de control de excepciones que usa el compilador, cuándo deben optimizarse las comprobaciones de excepciones y si se destruirán los objetos de C++ que quedan fuera del ámbito debido a una excepción. Si no se especifica **/EH,** el compilador permite que el código detecte excepciones estructuradas asincrónicas y excepciones C++, pero no destruye objetos C++ que salen del ámbito debido a una excepción asincrónica.

## <a name="syntax"></a>Sintaxis

> **/EH****á s**|**a**sá[**-****c**][**r**][ ]

## <a name="arguments"></a>Argumentos

**Un**<br/>
El modelo de control de excepciones que detecta excepciones asincrónicas (estructuradas) `catch(...)` y sincrónicas (C++) mediante el uso de la sintaxis De++.

**s**<br/>
El modelo de control de excepciones que detecta solo excepciones sincrónicas (C++) e indica al compilador que suponga que las funciones declaradas como **extern "C"** pueden producir una excepción.

**C**<br/>
Si se usa con **s** (**/EHsc**), solo detecta excepciones C++ e indica al compilador que suponga que las funciones declaradas como **extern "C"** nunca producen una excepción C++. **/EHca** es equivalente a **/EHa**.

**R**<br/>
Indica al compilador que siempre genere comprobaciones de terminación en tiempo de ejecución para todas las funciones **noexcept.** De forma predeterminada, las comprobaciones en tiempo de ejecución de **noexcept** se pueden optimizar si el compilador determina que la función solo llama a funciones que no son de lanzamiento.

## <a name="remarks"></a>Observaciones

La opción del compilador **/EHa** se usa para admitir el control de excepciones estructuradas asincrónicas (SEH) con la cláusula nativa de C++ `catch(...)` . Para implementar SEH sin especificar **/EHa**, puede utilizar la sintaxis **__try**, **__except**y **__finally.** Aunque Windows y Visual C++ admiten SEH, se recomienda encarecidamente utilizar el control de excepciones de C++, que se ajusta a la norma ISO (**/EHs** o **/EHsc**), ya que hace que el código sea más portátil y flexible. Sin embargo, en el código existente o para determinados tipos de programas (por ejemplo, en código compilado para admitir Common Language Runtime ([/clr (Common Language Runtime Compilation)),](clr-common-language-runtime-compilation.md)es posible que tenga que usar SEH. Para obtener más información, vea [Structured Exception Handling (C/C++)](../../cpp/structured-exception-handling-c-cpp.md).

Puede ser peligroso especificar **/EHa** e intentar controlar todas las excepciones mediante `catch(...)` . En la mayoría de los casos, las excepciones asincrónicas son irrecuperables y podrían considerarse fatales. La detección y continuidad de estas excepciones puede dañar el proceso y generar errores que son difíciles de encontrar y corregir.

Si utiliza **/EHs** o **/EHsc**, la cláusula `catch(...)` no detectará las excepciones estructuradas asincrónicas. Las infracciones de acceso y las excepciones <xref:System.Exception?displayProperty=fullName> administradas no se detectan, y, cuando se genera una excepción asincrónica, los objetos de no se destruyen, incluso aunque se controle esta excepción asincrónica.

Si usa **/EHa**, la imagen puede ser más grande y puede funcionar menos bien porque el compilador no optimiza un bloque **try** de forma tan agresiva. También deja filtros de excepción que llaman automáticamente a los destructores de todos los objetos locales aunque el compilador no vea ningún código que pueda producir una excepción de C++. De este modo, la pila puede desenredarse con seguridad en las excepciones asincrónicas, así como en las excepciones de C++. Cuando se usa **/EHs**, el compilador asume que las excepciones solo pueden producirse en una instrucción **throw** o en una llamada de función. Esto permite que el compilador elimine el código para realizar el seguimiento de vida útil de muchos objetos que no se pueden desenredar, y esto puede reducir significativamente el tamaño del código.

Se recomienda no vincular objetos compilados mediante **/EHa** junto con objetos compilados mediante **/EHs** o **/EHsc** en el mismo módulo ejecutable. Si tiene que controlar una excepción asincrónica mediante **/EHa** en cualquier parte del módulo, use **/EHa** para compilar todo el código del módulo. Puede usar la sintaxis de control de excepciones estructurada en el mismo módulo que el código compilado mediante **/EHs**, pero no puede mezclar la sintaxis SEH con **try**, **throw**y **catch** en la misma función.

Use **/EHa** si desea detectar una excepción provocada por algo distinto de un **lanzamiento**. En este ejemplo se genera y se detecta una excepción estructurada:

```cpp
// compiler_options_EHA.cpp
// compile with: /EHa
#include <iostream>
#include <excpt.h>
using namespace std;

void fail() {   // generates SE and attempts to catch it using catch(...)
   try {
      int i = 0, j = 1;
      j /= i;   // This will throw a SE (divide by zero).
      printf("%d", j);
   }
   catch(...) {   // catch block will only be executed under /EHa
      cout<<"Caught an exception in catch(...)."<<endl;
   }
}

int main() {
   __try {
      fail();
   }

   // __except will only catch an exception here
   __except(EXCEPTION_EXECUTE_HANDLER) {
      // if the exception was not caught by the catch(...) inside fail()
      cout << "An exception was caught in __except." << endl;
   }
}
```

La opción **/EHc** requiere que se haya especificado **/EHs** o **/EHa** . La opción **/clr** implica **/EHa** (es decir, **/clr** **/EHa** es redundante). El compilador genera un error si **/EHs** o **/EHsc** se utiliza después de **/clr**. Las optimizaciones no afectan a este comportamiento. Cuando se detecta una excepción, el compilador invoca al destructor o a los destructores de clase correspondientes a los objetos que están en el mismo ámbito que la excepción. Si no se detecta ninguna excepción, no se ejecutan estos destructores.

Para obtener información sobre las restricciones del control de excepciones en **/clr**, consulte [_set_se_translator](../../c-runtime-library/reference/set-se-translator.md).

La opción se puede desactivar **-** utilizando el símbolo . Por ejemplo, **/EHsc-** se interpreta como **/EHs** **/EHc-** y es equivalente a **/EHs**.

La opción del compilador **/EHr** fuerza las comprobaciones de terminación en tiempo de ejecución en todas las funciones que tienen un atributo **noexcept.** De forma predeterminada, las comprobaciones en tiempo de ejecución pueden optimizarse si el back-end del compilador determina que una función solo llame a funciones que *no producen excepciones* . Dichas funciones se componen de cualquier función que tiene un atributo que especifica que no se puede producir ninguna excepción. Esto incluye funciones marcadas como **noexcept** `throw()`, `__declspec(nothrow)`, , y, cuando se especifica **/EHc,** funciones **extern "C".** Las funciones que no producen excepciones también incluyen aquellas funciones que el compilador ha determinado que no producen excepciones durante la inspección. Se puede establecer explícitamente el valor predeterminado mediante **/EHr-**.

Sin embargo, el atributo que no produce excepciones no garantiza que una función no pueda producirlas. A diferencia del comportamiento de una función **noexcept,** el compilador MSVC considera una excepción iniciada por una función declarada mediante `throw()`, `__declspec(nothrow)`, o **extern "C"** como un comportamiento indefinido. Las funciones que usan estos tres atributos de la declaración no exigen comprobaciones de terminación en tiempo de ejecución para las excepciones. Puede usar la opción **/EHr** para ayudarle a identificar este comportamiento indefinido, forzando al compilador a generar comprobaciones en tiempo de ejecución para las excepciones no controladas que escapen a una función **noexcept.**

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener detalles, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Seleccione **Propiedades** > de configuración**C/C++** > **Generación**de código .

1. Modifique la propiedad **Habilitar excepciones de C++** .

   O bien, establezca **Habilitar excepciones de C++** en **No**y, en la página de propiedades **Línea de comandos** , en el cuadro **Opciones adicionales** , agregue la opción del compilador.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ExceptionHandling%2A>.

## <a name="see-also"></a>Consulte también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de línea de comandos del compilador MSVC](compiler-command-line-syntax.md)<br/>
[Controlar errores y excepciones](../../cpp/errors-and-exception-handling-modern-cpp.md)<br/>
[Especificaciones de excepción (lanzamiento)](../../cpp/exception-specifications-throw-cpp.md)<br/>
[Control de excepciones estructurado (C/C++)](../../cpp/structured-exception-handling-c-cpp.md)
