---
title: /RTC (Comprobaciones de errores en tiempo de ejecución)
ms.date: 11/04/2016
f1_keywords:
- /rtc
- VC.Project.VCCLCompilerTool.SmallerTypeCheck
- VC.Project.VCCLCompilerTool.UninitializedVariableCheck
- VC.Project.VCCLCompilerTool.StackFrameCheck
- VC.Project.VCCLCompilerTool.BasicRuntimeChecks
helpviewer_keywords:
- /RTCs compiler option [C++]
- -RTC1 compiler option [C++]
- run-time errors, error checks
- -RTCu compiler option [C++]
- /RTC1 compiler option [C++]
- /RTCc compiler option [C++]
- /RTCu compiler option [C++]
- __MSVC_RUNTIME_CHECKS macro
- -RTCs compiler option [C++]
- RTCs compiler option
- RTC1 compiler option
- run-time errors, run-time checks
- run-time checks, /RTC option
- RTCu compiler option
- RTCc compiler option
- -RTCc compiler option [C++]
ms.assetid: 9702c558-412c-4004-acd5-80761f589368
ms.openlocfilehash: a830ff5b8ba4b7fcd95eb462f899f2eadce6de11
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57815897"
---
# <a name="rtc-run-time-error-checks"></a>/RTC (Comprobaciones de errores en tiempo de ejecución)

Se utiliza para habilitar y deshabilitar la característica de comprobaciones de errores de tiempo de ejecución, junto con el [runtime_checks](../../preprocessor/runtime-checks.md) pragma.

## <a name="syntax"></a>Sintaxis

```
/RTC1
/RTCc
/RTCs
/RTCu
```

## <a name="arguments"></a>Argumentos

**1**<br/>
Equivalente de **/RTC**`su`.

**c**<br/>
Los informes cuando el valor se asigna a un tipo de datos más pequeño y los resultados en una pérdida de datos. Por ejemplo, si un valor de tipo `short 0x101` se asigna a una variable de tipo `char`.

Esta opción notifica situaciones en la que se va a truncar, por ejemplo, si desea que los ocho primeros bits de un `int` devuelve como un `char`. Dado que **/RTC** `c` provoca un error de tiempo de ejecución si toda la información se pierde como resultado de la asignación, se puede enmascarar la información que necesita para evitar un error en tiempo de ejecución como resultado de **/RTC** `c`. Por ejemplo:

```
#include <crtdbg.h>

char get8bits(int value, int position) {
   _ASSERT(position < 32);
   return (char)(value >> position);
   // Try the following line instead:
   // return (char)((value >> position) & 0xff);
}

int main() {
   get8bits(12341235,3);
}
```

**s**<br/>
Permite comprobaciones marco de pila error de tiempo de ejecución, como sigue:

- Inicialización de variables locales en un valor distinto de cero. Esto ayuda a identificar los errores que no aparecen cuando se ejecuta en modo de depuración. Hay una mayor probabilidad de que las variables de pila será cero en una compilación de depuración en comparación con una versión de lanzamiento debido a optimizaciones del compilador de las variables de pila en una versión de lanzamiento. Una vez que un programa ha utilizado un área de la pila, nunca se restablece en 0 por el compilador. Por lo tanto, las variables de pila posteriores sin inicializar que usen la misma área de pila pueden devolver valores restantes del uso anterior de esta memoria de pila.

- Detección de saturaciones y agotamientos de variables locales como matrices. **/ RTC** `s` no detectará las saturaciones al obtener acceso a memoria que resulta de relleno del compilador dentro de una estructura. Relleno podría producir mediante [alinear](../../cpp/align-cpp.md), [/Zp (alineación de miembros de Struct)](zp-struct-member-alignment.md), o [pack](../../preprocessor/pack.md), o si se ordenan los elementos de estructura de tal forma que requieren el compilador agregar relleno.

- Comprobación del puntero de pila, que detecta los daños del puntero de pila. Puntero de pila está dañada puede deberse a una incoherencia de convención de llamada. Por ejemplo, mediante un puntero a función, llamar a una función en un archivo DLL que se exporta como [__stdcall](../../cpp/stdcall.md) pero se declara el puntero a la función como [__cdecl](../../cpp/cdecl.md).

**u**<br/>
Indica cuándo se usa una variable sin haberse inicializado. Por ejemplo, una instrucción que genera `C4701` también se puede generar un error en tiempo de ejecución bajo **/RTC**`u`. Cualquier instrucción que genere [advertencia del compilador (niveles 1 y 4) C4700](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md) generará un error en tiempo de ejecución bajo **/RTC**`u`.

Sin embargo, tenga en cuenta el siguiente fragmento de código:

```cpp
int a, *b, c;
if ( 1 )
b = &a;
c = a;  // No run-time error with /RTCu
```

Si una variable se ha inicializado, no se notificarán en tiempo de ejecución **/RTC**`u`. Por ejemplo, después de una variable es un alias a través de un puntero, el compilador no realizar un seguimiento de la variable y de informes utiliza sin inicializar. De hecho, puede inicializar una variable por tomar su dirección. El & operador funciona como un operador de asignación en esta situación.

## <a name="remarks"></a>Comentarios

Comprobaciones de errores en tiempo de ejecución son una manera de encontrar problemas en su código en ejecución. Para obtener más información, vea [Cómo: Uso de comprobaciones nativas en tiempo de ejecución](/visualstudio/debugger/how-to-use-native-run-time-checks).

Si compila el programa en la línea de comandos mediante cualquiera de los **/RTC** opciones del compilador, cualquier directiva pragma [optimizar](../../preprocessor/optimize.md) instrucciones que aparecen en el código en modo silencioso se producirá un error. Esto es porque las comprobaciones de errores en tiempo de ejecución no son válidas en una compilación de versión (optimizado).

Debe usar **/RTC** para las compilaciones de desarrollo; **/RTC** no debe usarse para una compilación comercial. **/ RTC** no se puede usar con las optimizaciones del compilador ([opciones /O (optimizar código)](o-options-optimize-code.md)). Crea una imagen de programa con **/RTC** será un poco más grande y ligeramente más lenta que una imagen creada con **/Od** (hasta 5 por ciento más lento que una **/Od** compilar).

Cuando usas cualquiera, se definirá la directiva de preprocesador __MSVC_RUNTIME_CHECKS **/RTC** opción o [/GZ](gz-enable-stack-frame-run-time-error-checking.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Haga clic en la carpeta **C/C++** .

1. Haga clic en el **generación de código** página de propiedades.

1. Modifique una o ambas de las siguientes propiedades: **Comprobaciones básicas en tiempo de ejecución** o **comprobación de tipo más pequeño**.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea las propiedades <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BasicRuntimeChecks%2A> y <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.SmallerTypeCheck%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador MSVC](compiler-options.md)<br/>
[Sintaxis de línea de comandos del compilador MSVC](compiler-command-line-syntax.md)<br/>
[Cómo: Uso de comprobaciones nativas en tiempo de ejecución](/visualstudio/debugger/how-to-use-native-run-time-checks)
