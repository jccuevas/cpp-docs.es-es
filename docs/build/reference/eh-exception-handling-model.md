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
ms.openlocfilehash: 9f5eed60ecb51abc1d8fbd3c38773bbf782b23a5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62271806"
---
# <a name="eh-exception-handling-model"></a>/EH (Modelo de control de excepciones)

Especifica el tipo de control de excepciones que usa el compilador, cuándo deben optimizarse las comprobaciones de excepciones y si se destruirán los objetos de C++ que quedan fuera del ámbito debido a una excepción. Si **/EH** no se especifica, el compilador permite que el código detectar las excepciones estructuradas asincrónicas y las excepciones de C++, pero no destruirá los objetos de C++ que estén fuera del ámbito debido a una excepción asincrónica.

## <a name="syntax"></a>Sintaxis

> **/EH**{**s**|**a**}[**c**][**r**][**-**]

## <a name="arguments"></a>Argumentos

**a**<br/>
El modelo de control de excepciones que detecta las asincrónicas (estructuradas) y sincrónicas (C++) las excepciones mediante el uso de C++ `catch(...)` sintaxis.

**s**<br/>
El modelo de control de excepciones que detecta excepciones sincrónicas (C++) solo e indica al compilador que asuma que las funciones declaradas como **extern "C"** puede producir una excepción.

**c**<br/>
Si se usa con **s** (**/EHsc**), captura solo las excepciones de C++ e indica al compilador que asuma que las funciones declaradas como **extern "C"** jamás inician una excepción de C++. **/EHca** es equivalente a **/EHa**.

**r**<br/>
Indica al compilador que genere siempre las comprobaciones de terminación en tiempo de ejecución para todos los **noexcept** funciones. De forma predeterminada, en tiempo de ejecución busca **noexcept** pueden optimizarse si el compilador determina que la función llama a funciones sólo no producen excepciones.

## <a name="remarks"></a>Comentarios

La opción del compilador **/EHa** se usa para admitir el control de excepciones estructuradas asincrónicas (SEH) con la cláusula nativa de C++ `catch(...)` . Para implementar SEH sin especificar **/EHa**, puede usar el **__try**, **__except**, y **__finally** sintaxis. Aunque Windows y Visual C++ admiten SEH, se recomienda encarecidamente utilizar el control de excepciones de C++, que se ajusta a la norma ISO (**/EHs** o **/EHsc**), ya que hace que el código sea más portátil y flexible. No obstante, en el código existente o para determinados tipos de programas, por ejemplo, en el código compilado para admitir common language runtime ([/CLR (Common Language Runtime Compilation)](clr-common-language-runtime-compilation.md)), aún tendrá que usan SEH. Para obtener más información, vea [Structured Exception Handling (C/C++)](../../cpp/structured-exception-handling-c-cpp.md).

Puede ser peligroso especificar **/EHa** e intentar controlar todas las excepciones mediante `catch(...)` . En la mayoría de los casos, las excepciones asincrónicas son irrecuperables y podrían considerarse fatales. La detección y continuidad de estas excepciones puede dañar el proceso y generar errores que son difíciles de encontrar y corregir.

Si utiliza **/EHs** o **/EHsc**, la cláusula `catch(...)` no detectará las excepciones estructuradas asincrónicas. Las infracciones de acceso y las excepciones <xref:System.Exception?displayProperty=fullName> administradas no se detectan, y, cuando se genera una excepción asincrónica, los objetos de no se destruyen, incluso aunque se controle esta excepción asincrónica.

Si usas **/EHa**, la imagen podría ser más grande y no ejecutarse bien, ya que el compilador no optimiza un **intente** bloquear de forma tan agresiva. También deja filtros de excepción que llaman automáticamente a los destructores de todos los objetos locales aunque el compilador no vea ningún código que pueda producir una excepción de C++. De este modo, la pila puede desenredarse con seguridad en las excepciones asincrónicas, así como en las excepciones de C++. Cuando usas **/EHs**, el compilador supone que solo pueden producirse excepciones en un **throw** declaración o en una llamada de función. Esto permite que el compilador elimine el código para realizar el seguimiento de vida útil de muchos objetos que no se pueden desenredar, y esto puede reducir significativamente el tamaño del código.

Es recomendable que no vincule objetos compilados mediante **/EHa** junto con objetos compilados mediante **/EHs** o **/EHsc** en el mismo módulo ejecutable. Si tiene que controlar una excepción asincrónica mediante **/EHa** en cualquier parte del módulo, use **/EHa** para compilar todo el código del módulo. Puede usar la sintaxis en el mismo módulo que el código que se compila mediante el uso del control de excepciones estructurado **/EHs**, pero no se pueden mezclar la sintaxis de SEH con **intente**, **throw**y **catch** en la misma función.

Use **/EHa** si desea detectar una excepción producida por algo distinto de un **throw**. En este ejemplo se genera y se detecta una excepción estructurada:

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

La opción **/EHc** requiere que se haya especificado **/EHs** o **/EHa** . El **/CLR** opción implica **/EHa** (es decir, **/CLR** **/EHa** es redundante). El compilador genera un error si **/EHs** o **/EHsc** se usa después **/CLR**. Las optimizaciones no afectan a este comportamiento. Cuando se detecta una excepción, el compilador invoca al destructor o a los destructores de clase correspondientes a los objetos que están en el mismo ámbito que la excepción. Si no se detecta ninguna excepción, no se ejecutan estos destructores.

Para obtener información sobre las restricciones del control de excepciones en **/clr**, consulte [_set_se_translator](../../c-runtime-library/reference/set-se-translator.md).

La opción puede eliminarse mediante el símbolo **-**. Por ejemplo, **/EHsc-** se interpreta como **/EHs** **/EHc-** y es equivalente a **/EHs**.

El **/EHr** opción del compilador fuerza las comprobaciones de terminación en tiempo de ejecución en todas las funciones que tienen un **noexcept** atributo. De forma predeterminada, las comprobaciones en tiempo de ejecución pueden optimizarse si el back-end del compilador determina que una función solo llame a funciones que *no producen excepciones* . Dichas funciones se componen de cualquier función que tiene un atributo que especifica que no se puede producir ninguna excepción. Esto incluye las funciones marcadas como **noexcept**, `throw()`, `__declspec(nothrow)`y cuándo **/EHc** se especifica, **extern "C"** funciones. Las funciones que no producen excepciones también incluyen aquellas funciones que el compilador ha determinado que no producen excepciones durante la inspección. Se puede establecer explícitamente el valor predeterminado mediante **/EHr-**.

Sin embargo, el atributo que no produce excepciones no garantiza que una función no pueda producirlas. A diferencia del comportamiento de un **noexcept** función, el compilador MSVC considera que una excepción producida por una función declarada mediante `throw()`, `__declspec(nothrow)`, o **extern "C"** como un comportamiento indefinido. Las funciones que usan estos tres atributos de la declaración no exigen comprobaciones de terminación en tiempo de ejecución para las excepciones. Puede usar el **/EHr** opción que le ayudarán a identificar este un comportamiento indefinido, al forzar el compilador genere comprobaciones en tiempo de ejecución para las excepciones no controladas que eluden una **noexcept** función.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Seleccione **propiedades de configuración** > **C o C++** > **generación de código**.

1. Modifique la propiedad **Habilitar excepciones de C++** .

   O bien, establezca **Habilitar excepciones de C++** en **No**y, en la página de propiedades **Línea de comandos** , en el cuadro **Opciones adicionales** , agregue la opción del compilador.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ExceptionHandling%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)<br/>
[Controlar errores y excepciones](../../cpp/errors-and-exception-handling-modern-cpp.md)<br/>
[Especificaciones de excepciones (throw)](../../cpp/exception-specifications-throw-cpp.md)<br/>
[Control de excepciones estructurado (C/C++)](../../cpp/structured-exception-handling-c-cpp.md)
