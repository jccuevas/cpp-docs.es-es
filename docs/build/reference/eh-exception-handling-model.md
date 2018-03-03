---
title: -EH (modelo de control de excepciones) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLWCECompilerTool.ExceptionHandling
- /eh
- VC.Project.VCCLCompilerTool.ExceptionHandling
dev_langs:
- C++
helpviewer_keywords:
- exception handling, compiler model
- cl.exe compiler, exception handling
- EH compiler option [C++]
- -EH compiler option [C++]
- /EH compiler option [C++]
ms.assetid: 754b916f-d206-4472-b55a-b6f1b0f2cb4d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1c56020d5013e951d9d43ed799d34641d114d612
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="eh-exception-handling-model"></a>/EH (Modelo de control de excepciones)
Especifica el tipo de control de excepciones que usa el compilador, cuándo deben optimizarse las comprobaciones de excepciones y si se destruirán los objetos de C++ que quedan fuera del ámbito debido a una excepción. Si no se especifica **/EH** , el compilador detectará tanto las excepciones estructuradas asincrónicas como las excepciones de C++, pero no destruirá los objetos de C++ que estén fuera de ámbito debido a una excepción asincrónica.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/EH{s|a}[c][r][-]  
```  
  
## <a name="arguments"></a>Argumentos  
 **a**  
 Modelo de control de excepciones que detecta las excepciones asincrónicas (estructuradas) y sincrónicas (C++).  
  
 **s**  
 Modelo de control de excepciones que solo detecta las excepciones de C++ e indica al compilador que presuponga que las funciones declaradas como `extern "C"` pueden generar una excepción.  
  
 **c**  
 Si se utiliza con **s** (**/EHsc**), captura solo las excepciones de C++ e indica al compilador que suponga que las funciones declaradas como `extern "C"` jamás inician una excepción de C++.  
  
 **/EHca** es equivalente a **/EHa**.  
  
 **r**  
 Indica al compilador que genere siempre las comprobaciones de terminación en tiempo de ejecución para todas las funciones `noexcept` . De forma predeterminada, las comprobaciones en tiempo de ejecución para `noexcept` pueden optimizarse si el compilador determina que la función solo llame a funciones que no producen excepciones.  
  
## <a name="remarks"></a>Comentarios  
 La opción del compilador **/EHa** se usa para admitir el control de excepciones estructuradas asincrónicas (SEH) con la cláusula nativa de C++ `catch(...)` . Para implementar SEH sin especificar **/EHa**, puede utilizar la sintaxis `__try`, `__except`y `__finally` . Aunque Windows y Visual C++ admiten SEH, se recomienda encarecidamente utilizar el control de excepciones de C++, que se ajusta a la norma ISO (**/EHs** o **/EHsc**), ya que hace que el código sea más portátil y flexible. No obstante, en el código existente o en determinados tipos de programas, por ejemplo, en el código compilado para admitir common language runtime ([/clr (compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)), quizás tenga que seguir utilizando SEH. Para obtener más información, vea [Structured Exception Handling (C/C++)](../../cpp/structured-exception-handling-c-cpp.md).  
  
 Puede ser peligroso especificar **/EHa** e intentar controlar todas las excepciones mediante `catch(...)` . En la mayoría de los casos, las excepciones asincrónicas son irrecuperables y podrían considerarse fatales. La detección y continuidad de estas excepciones puede dañar el proceso y generar errores que son difíciles de encontrar y corregir.  
  
 Si utiliza **/EHs** o **/EHsc**, la cláusula `catch(...)` no detectará las excepciones estructuradas asincrónicas. Las infracciones de acceso y las excepciones <xref:System.Exception?displayProperty=fullName> administradas no se detectan, y, cuando se genera una excepción asincrónica, los objetos de no se destruyen, incluso aunque se controle esta excepción asincrónica.  
  
 Si utiliza **/EHa**, la imagen podría ser más grande y no ejecutarse bien, ya que el compilador no optimiza un bloque `try` de forma tan agresiva. También deja filtros de excepción que llaman automáticamente a los destructores de todos los objetos locales aunque el compilador no vea ningún código que pueda producir una excepción de C++. De este modo, la pila puede desenredarse con seguridad en las excepciones asincrónicas, así como en las excepciones de C++. Cuando se usa **/EHs**, el compilador presupone que las excepciones solo pueden producirse en una instrucción `throw` o en una llamada de función. Esto permite que el compilador elimine el código para realizar el seguimiento de vida útil de muchos objetos que no se pueden desenredar, y esto puede reducir significativamente el tamaño del código.  
  
 Es recomendable que no vincule objetos compilados mediante **/EHa** con objetos compilados mediante **/EHs** en el mismo módulo ejecutable. Si tiene que controlar una excepción asincrónica mediante **/EHa** en cualquier parte del módulo, use **/EHa** para compilar todo el código del módulo. Puede utilizar la sintaxis del control de excepciones estructurado en el mismo módulo que el código compilado mediante **/EHs**, pero no puede combinar la sintaxis de SEH con `try`, `throw`y `catch` en la misma función.  
  
 Utilice **/EHa** si desea detectar una excepción producida por un método distinto de `throw`. En este ejemplo se genera y se detecta una excepción estructurada:  
  
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
  
 La opción **/EHc** requiere que se haya especificado **/EHs** o **/EHa** . La opción **/clr** implica **/EHa** (es decir, **/clr /EHa** es redundante). El compilador genera un error si **/EHs[c]** se utiliza después de **/clr**. Las optimizaciones no afectan a este comportamiento. Cuando se detecta una excepción, el compilador invoca al destructor o a los destructores de clase correspondientes a los objetos que están en el mismo ámbito que la excepción. Si no se detecta ninguna excepción, no se ejecutan estos destructores.  
  
 Para obtener información sobre las restricciones del control de excepciones en **/clr**, consulte [_set_se_translator](../../c-runtime-library/reference/set-se-translator.md).  
  
 La opción puede eliminarse mediante el símbolo **-**. Por ejemplo, **/EHsc-** se interpreta como **/EHs /EHc-** y es equivalente a **/EHs**.  
  
 La opción del compilador **/EHr** fuerza las comprobaciones de terminación en tiempo de ejecución en todas las funciones que tienen un atributo `noexcept` . De forma predeterminada, las comprobaciones en tiempo de ejecución pueden optimizarse si el back-end del compilador determina que una función solo llame a funciones que *no producen excepciones* . Dichas funciones se componen de cualquier función que tiene un atributo que especifica que no se puede producir ninguna excepción. Esto incluye las funciones marcadas como `noexcept`, `throw()`, `__declspec(nothrow)`y, si se especifica **/EHc** , las funciones `extern "C"` . Las funciones que no producen excepciones también incluyen aquellas funciones que el compilador ha determinado que no producen excepciones durante la inspección. Se puede establecer explícitamente el valor predeterminado mediante **/EHr-**.  
  
 Sin embargo, el atributo que no produce excepciones no garantiza que una función no pueda producirlas. A diferencia del comportamiento de una función `noexcept` , el compilador de Visual C++ considera que una excepción producida por una función declarada mediante `throw()`, `__declspec(nothrow)`o `extern "C"` como un comportamiento indefinido. Las funciones que usan estos tres atributos de la declaración no exigen comprobaciones de terminación en tiempo de ejecución para las excepciones. Se puede usar la opción **/EHr** para ayudar a identificar este comportamiento indefinido, al forzar al compilador para que genere comprobaciones en tiempo de ejecución para las excepciones no controladas que eluden una función `noexcept` .  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  En el panel izquierdo, expanda **Propiedades de configuración**, **C/C++**y **Generación de código**.  
  
3.  Modifique la propiedad **Habilitar excepciones de C++** .  
  
     O bien, establezca **Habilitar excepciones de C++** en **No**y, en la página de propiedades **Línea de comandos** , en el cuadro **Opciones adicionales** , agregue la opción del compilador.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ExceptionHandling%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)   
 [Controlar errores y excepciones](../../cpp/errors-and-exception-handling-modern-cpp.md)   
 [Especificaciones de excepciones (throw)](../../cpp/exception-specifications-throw-cpp.md)   
 [Control de excepciones estructurado (C/C++)](../../cpp/structured-exception-handling-c-cpp.md)