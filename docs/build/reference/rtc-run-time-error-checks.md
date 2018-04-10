---
title: -/RTC (comprobaciones de errores en tiempo de ejecución) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- /rtc
- VC.Project.VCCLCompilerTool.SmallerTypeCheck
- VC.Project.VCCLCompilerTool.UninitializedVariableCheck
- VC.Project.VCCLCompilerTool.StackFrameCheck
- VC.Project.VCCLCompilerTool.BasicRuntimeChecks
dev_langs:
- C++
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
caps.latest.revision: 18
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8699a96dcd7c04bc1b2707e964afb4b68068147e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="rtc-run-time-error-checks"></a>/RTC (Comprobaciones de errores en tiempo de ejecución)
Usar para habilitar y deshabilitar la característica de comprobaciones de errores de tiempo de ejecución, junto con el [runtime_checks](../../preprocessor/runtime-checks.md) pragma.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/RTC1  
/RTCc  
/RTCs  
/RTCu  
```  
  
## <a name="arguments"></a>Argumentos  
 `1`  
 Equivalente de **/RTC**`su`.  
  
 `c`  
 Informes cuando un valor que se asigna a un tipo de datos más pequeño y da como resultado una pérdida de datos. Por ejemplo, si un valor de tipo `short 0x101` se asigna a una variable de tipo `char`.  
  
 Esta opción informa de situaciones en que se va a truncar datos, por ejemplo, si desea que los ocho primeros bits de un `int` formando una `char`. Dado que **/RTC** `c` provoca un error de tiempo de ejecución si toda la información se pierde como resultado de la asignación, puede enmascarar la información que necesita para evitar un error en tiempo de ejecución como resultado de **/RTC** `c`. Por ejemplo:  
  
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
  
 `s`  
 Habilita la comprobación de la pila marco error de tiempo de ejecución, como se indica a continuación:  
  
-   Inicialización de variables locales a un valor distinto de cero. Esto ayuda a identificar los errores que no aparecen cuando se ejecuta en modo de depuración. Hay una mayor probabilidad de que las variables de pila sigan siendo cero en una compilación de depuración en comparación con una versión de lanzamiento debido a optimizaciones del compilador de las variables de pila en una versión de lanzamiento. Una vez que un programa ha utilizado un área de la pila, nunca se restablece a 0 por el compilador. Por lo tanto, las variables de pila posteriores sin inicializar que usen la misma área de pila pueden devolver valores restantes de las ejecuciones anteriores de la memoria de la pila.  
  
-   Detección de saturaciones y agotamientos de variables locales como matrices. **/ RTC** `s` no detecta las saturaciones cuando obtiene acceso a memoria que es el resultado del relleno del compilador dentro de una estructura. Relleno podría producir mediante [alinear](../../cpp/align-cpp.md), [/Zp (alineación de miembros de Struct)](../../build/reference/zp-struct-member-alignment.md), o [pack](../../preprocessor/pack.md), o si se ordenan los elementos de estructura de manera que se exija al compilador agregar relleno.  
  
-   Comprobación del puntero de pila, que detecta los daños de puntero de pila. Daños en el puntero pila pueden deberse a una incoherencia de convención de llamada. Por ejemplo, utiliza un puntero a función, puede llamar a una función en un archivo DLL que se exporta como [__stdcall](../../cpp/stdcall.md) , pero el puntero a la función que se declara [__cdecl](../../cpp/cdecl.md).  
  
 `u`  
 Informes cuando se usa una variable sin haberse inicializado. Por ejemplo, una instrucción que genera `C4701` también se puede generar un error en tiempo de ejecución bajo **/RTC**`u`. Cualquier instrucción que genere [advertencia del compilador (niveles 1 y 4) C4700](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md) generará un error en tiempo de ejecución bajo **/RTC**`u`.  
  
 Sin embargo, tenga en cuenta el siguiente fragmento de código:  
  
```cpp  
int a, *b, c;  
if ( 1 )  
b = &a;  
c = a;  // No run-time error with /RTCu  
```  
  
 Si una variable se ha inicializado, no se notificarán en tiempo de ejecución por **/RTC**`u`. Por ejemplo, después de una variable es un alias a través de un puntero, el compilador se realizar un seguimiento de la variable no y de informes utiliza sin inicializar. De hecho, se puede inicializar una variable al tomar su dirección. La & operador funciona como un operador de asignación en esta situación.  
  
## <a name="remarks"></a>Comentarios  
 Comprobaciones de errores en tiempo de ejecución son una manera de buscar problemas en el código en ejecución. Para obtener más información, consulte [Cómo: uso de comprobaciones en tiempo de ejecución nativo](/visualstudio/debugger/how-to-use-native-run-time-checks).  
  
 Si compila el programa en la línea de comandos mediante cualquiera de los **/RTC** opciones del compilador, cualquier directiva pragma [optimizar](../../preprocessor/optimize.md) instrucciones en el código en modo silencioso se producirá un error. Esto es porque las comprobaciones de errores en tiempo de ejecución no son válidas en una compilación de versión (optimizado).  
  
 Debe usar **/RTC** para las compilaciones de desarrollo; **/RTC** no debe usarse para una compilación comercial. **/ RTC** no se puede usar con las optimizaciones del compilador ([opciones /O (optimizar código)](../../build/reference/o-options-optimize-code.md)). Crea una imagen de programa con **/RTC** será ligeramente mayor y ligeramente más lenta que una imagen creada con **/Od** (hasta 5 por ciento más lenta que una **/Od** compilar).  
  
 Cuando se utiliza alguno, se definirá la directiva de preprocesador __MSVC_RUNTIME_CHECKS **/RTC** opción o [/GZ](../../build/reference/gz-enable-stack-frame-run-time-error-checking.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **C/C++** .  
  
3.  Haga clic en el **generación de código** página de propiedades.  
  
4.  Modificar una o ambas de las siguientes propiedades: **comprobaciones en tiempo de ejecución básicas** o **comprobación de tipos más pequeños**.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación  
  
-   Vea las propiedades <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BasicRuntimeChecks%2A> y <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.SmallerTypeCheck%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)   
 [Cómo: Usar comprobaciones nativas en tiempo de ejecución](/visualstudio/debugger/how-to-use-native-run-time-checks)