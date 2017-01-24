---
title: "/RTC (Comprobaciones de errores en tiempo de ejecuci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/rtc"
  - "VC.Project.VCCLCompilerTool.SmallerTypeCheck"
  - "VC.Project.VCCLCompilerTool.UninitializedVariableCheck"
  - "VC.Project.VCCLCompilerTool.StackFrameCheck"
  - "VC.Project.VCCLCompilerTool.BasicRuntimeChecks"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/RTC1 (opción del compilador) [C++]"
  - "/RTCc (opción del compilador) [C++]"
  - "/RTCs (opción del compilador) [C++]"
  - "/RTCu (opción del compilador) [C++]"
  - "__MSVC_RUNTIME_CHECKS (macro)"
  - "RTC1 (opción del compilador)"
  - "-RTC1 (opción del compilador) [C++]"
  - "RTCc (opción del compilador)"
  - "-RTCc (opción del compilador) [C++]"
  - "RTCs (opción del compilador)"
  - "-RTCs (opción del compilador) [C++]"
  - "RTCu (opción del compilador)"
  - "-RTCu (opción del compilador) [C++]"
  - "comprobaciones en tiempo de ejecución, /RTC (opción)"
  - "errores en tiempo de ejecución, comprobaciones de errores"
  - "errores en tiempo de ejecución, comprobaciones en tiempo de ejecución"
ms.assetid: 9702c558-412c-4004-acd5-80761f589368
caps.latest.revision: 18
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /RTC (Comprobaciones de errores en tiempo de ejecuci&#243;n)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Se utiliza para habilitar y deshabilitar la característica de comprobaciones de errores en tiempo de ejecución, junto con el pragma [runtime\_checks](../../preprocessor/runtime-checks.md).  
  
## Sintaxis  
  
```  
/RTC1  
/RTCc  
/RTCs  
/RTCu  
```  
  
## Argumentos  
 `1`  
 Equivalente a **\/RTC**`su`.  
  
 `c`  
 Comunica los casos en que se asigna un valor a un tipo de datos más pequeño y causa una pérdida de datos.  Por ejemplo, si un valor de tipo `short 0x101` se asigna a una variable de tipo `char`.  
  
 Esta opción informa de situaciones en las que se pretende truncar, por ejemplo, si se desea devolver los ocho primeros bits de un valor `int` como `char`.  Dado que **\/RTC**`c` causa un error en tiempo de ejecución si se pierde información como consecuencia de la asignación, es posible enmascarar la información que necesite para evitarse errores en tiempo de ejecución como resultado de **\/RTC**`c`.  Por ejemplo:  
  
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
 Habilita las comprobaciones de errores en tiempo de ejecución en el marco de pila, como se indica a continuación:  
  
-   Inicialización de variables locales a un valor distinto de cero.  Ayuda a identificar los errores que no aparecen durante la ejecución en modo de depuración.  La posibilidad de que las variables de pila sigan siendo cero es mayor en una generación de depuración si se compara con una generación de lanzamiento, a causa de las optimizaciones por el compilador de las variables de pila en una generación de lanzamiento.  Cuando un programa ha utilizado un área de su pila, el compilador nunca la repone a 0.  Por lo tanto, las variables de pila posteriores sin inicializar que usen la misma área de la pila pueden devolver valores que permanecen desde el uso anterior de esta memoria de pila.  
  
-   Detección de sobrecargas y ejecuciones insuficientes de variables locales como matrices.  **\/RTC**`s` no detectará las sobrecargas al tener acceso a la memoria que es el resultado del relleno del compilador dentro de una estructura.  El relleno podría producirse por el uso de [align](../../cpp/align-cpp.md), [\/Zp \(Alineación de miembros de estructura\)](../../build/reference/zp-struct-member-alignment.md) o [pack](../../preprocessor/pack.md), o bien si se ordenan elementos de la estructura de tal forma que ello exija al compilador agregar relleno.  
  
-   Comprobación de punteros de pila, que detecta los daños en los punteros de pila.  Dichos daños podrían deberse a un error de coincidencia en la convención de llamadas.  Por ejemplo, cuando se utiliza un puntero a función, puede llamar a una función de un archivo DLL que se exporta como [\_\_stdcall](../../cpp/stdcall.md), pero el puntero a la función se declara como [\_\_cdecl](../../cpp/cdecl.md).  
  
 `u`  
 Informa cuándo se usa una variable sin haberse inicializado.  Por ejemplo, una instrucción que genera `C4701` también puede generar un error en tiempo de ejecución bajo **\/RTC**`u`.  Cualquier instrucción que genere [Advertencia del compilador \(niveles 1 y 4\) C4700](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md) generará un error en tiempo de ejecución bajo **\/RTC**`u`.  
  
 Sin embargo, considere el fragmento de código siguiente:  
  
```  
int a, *b, c;  
if ( 1 )  
b = &a;  
c = a;  // No run-time error with /RTCu  
```  
  
 Si se hubiera podido inicializar una variable, no habría sido detectada en tiempo de ejecución por **\/RTC**`u`.  Por ejemplo, después de crear un alias de una variable por medio de un puntero, el compilador no hace un seguimiento de la variable ni comunica los usos sin inicialización.  En realidad, puede inicializar una variable si toma su dirección.  & El operador funciona como un operador de asignaciones en esta situación.  
  
## Comentarios  
 Las comprobaciones de errores en tiempo de ejecución son una manera de identificar problemas en el código en ejecución. Para obtener más información, vea [Cómo: Utilizar comprobaciones nativas en tiempo de ejecución](../Topic/How%20to:%20Use%20Native%20Run-Time%20Checks.md).  
  
 Si compila un programa en la línea de comandos con cualquiera de las opciones del compilador **\/RTC**, las instrucciones de pragma [optimize](../../preprocessor/optimize.md) del código producirán un error sin comunicarlo.  Esto ocurre porque las comprobaciones de errores en tiempo de ejecución no son válidas en una versión de lanzamiento \(optimizada\).  
  
 Debe utilizar **\/RTC** para compilaciones de desarrollo; no se debe utilizar **\/RTC** para una versión comercial.  **\/RTC** no se puede utilizar con optimizaciones del compilador \([\/O \(Opciones\) \(Optimizar código\)](../../build/reference/o-options-optimize-code.md)\).  Una imagen de un programa compilada con **\/RTC** tendrá un tamaño ligeramente mayor y será un poco más lenta que otra compilada con **\/Od** \(hasta un 5 por ciento más lenta que una versión de **\/Od**\).  
  
 La directiva de preprocesador \_\_MSVC\_RUNTIME\_CHECKS se define al utilizar una de las opciones **\/RTC** o [\/GZ](../../build/reference/gz-enable-stack-frame-run-time-error-checking.md).  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Haga clic en la carpeta **C\/C\+\+**.  
  
3.  Haga clic en la página de propiedades **Generación de código**.  
  
4.  Modifique una o las dos propiedades siguientes: **Comprobaciones básicas en tiempo de ejecución** o **Comprobación de tipos más pequeños**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea las propiedades <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BasicRuntimeChecks%2A> y <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.SmallerTypeCheck%2A>.  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)   
 [RTC sample](http://msdn.microsoft.com/es-es/b3415b09-f6fd-43dc-8c02-9a910bc2574e)