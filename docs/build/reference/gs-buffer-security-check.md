---
title: "/GS (Comprobaci&#243;n de seguridad del b&#250;fer) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLWCECompilerTool.BufferSecurityCheck"
  - "VC.Project.VCCLCompilerTool.BufferSecurityCheck"
  - "/GS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "búferes [C++], saturaciones del búfer"
  - "saturaciones del búfer, modificador /GS del compilador."
  - "GS (opción del compilador) [C++]"
  - "/GS (opción del compilador) [C++]"
  - "comprobación de seguridad (opción del compilador) [C++]"
  - "-GS (opción del compilador) [C++]"
  - "búferes [C++], evitar saturaciones"
ms.assetid: 8d8a5ea1-cd5e-42e1-bc36-66e1cd7e731e
caps.latest.revision: 40
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 40
---
# /GS (Comprobaci&#243;n de seguridad del b&#250;fer)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Detecta algunas saturaciones de búfer que sobrescriben la dirección de devolución de una función, la dirección del controlador de excepciones o ciertos tipos de parámetros.  Producir una saturación del búfer es una técnica utilizada por los piratas informáticos para aprovechar que el código no impone restricciones del tamaño de búfer.  
  
## Sintaxis  
  
```  
/GS[-]  
```  
  
## Comentarios  
 La opción **\/GS** está activada de manera predeterminada.  Si cree que la aplicación no se va a ver expuesta a ningún riesgo de seguridad, use **\/GS\-**.  Para obtener más información sobre **\/GS**, vea [Comprobación de seguridad exhaustiva del compilador](http://go.microsoft.com/fwlink/?linkid=7260).  Para obtener más información acerca de la supresión de la detección de saturación del búfer, vea [safebuffers](../../cpp/safebuffers.md).  
  
## Comprobaciones de seguridad  
 A las funciones que el compilador reconoce como propensas a problemas de saturación del búfer, les asigna espacio en la pila antes de la dirección de devolución.  En la entrada de la función, se carga una *cookie de seguridad* en el espacio asignado, que se procesa una vez durante la carga del módulo.  A la salida de la función, y durante el desenredo del marco en los sistemas operativos de 64 bits, se llama a una función auxiliar para asegurarse de que el valor de la cookie sigue siendo el mismo.  Un valor diferente indica que se puede haber producido una sobrescritura de la pila.  Si se detecta un valor diferente, se finaliza el proceso.  
  
## Búferes GS  
 Se realiza una comprobación de seguridad de saturación del búfer en un *búfer GS*.  Un búfer GS puede ser uno de los siguientes:  
  
-   Una matriz que tiene más de 4 bytes, más de dos elementos y un tipo de elemento que no es un tipo de puntero.  
  
-   Una estructura de datos cuyo tamaño es superior a 8 bytes y no contiene punteros.  
  
-   Un búfer asignado mediante la función [\_alloca](../../c-runtime-library/reference/alloca.md).  
  
-   Cualquier clase o estructura que contiene un búfer GS.  
  
 Por ejemplo, las siguientes instrucciones declaran los búferes GS.  
  
```  
char buffer[20];  
int buffer[20];  
struct { int a; int b; int c; int d; } myStruct;  
struct { int a; char buf[20]; };  
```  
  
 Sin embargo, las siguientes instrucciones no declaran búferes GS.  Las primeras dos declaraciones contienen elementos de tipo de puntero.  Las instrucciones tercera y cuarta declaran matrices cuyo tamaño es demasiado pequeño.  La quinta instrucción declara una estructura cuyo tamaño en una plataforma x86 no es superior a 8 bytes.  
  
```  
char *pBuf[20];  
void *pv[20];  
char buf[4];  
int buf[2];  
struct { int a; int b; };  
```  
  
## Inicializar la cookie de seguridad  
 La opción del compilador **\/GS** requiere que la cookie de seguridad se inicialice antes de ejecutar cualquier función que la utilice.  La cookie de seguridad se debe inicializar en la entrada a un archivo EXE o DLL.  Automáticamente se hace esto si utiliza los puntos de entrada predeterminados de CRT \(mainCRTStartup, wmainCRTStartup, WinMainCRTStartup, wWinMainCRTStartup o \_DllMainCRTStartup\).  Si usa un punto de entrada alternativo, debe inicializar manualmente la cookie de seguridad llamando a [\_\_security\_init\_cookie](../../c-runtime-library/reference/security-init-cookie.md).  
  
## Lo que está protegido  
 La opción del compilador **\/GS** protege los elementos siguientes:  
  
-   La dirección de devolución de una llamada de función.  
  
-   La dirección de un controlador de excepciones para una función.  
  
-   Parámetros de función vulnerables.  
  
 En todas las plataformas, **\/GS** intenta detectar saturaciones de búfer en la dirección de devolución.  Las saturaciones de búfer se aprovechan con mayor facilidad en plataformas como x86 y x64, que usan convenciones de llamada para almacenar la dirección de devolución de una llamada a función en la pila.  
  
 En x86, si una función usa un controlador de excepciones, el compilador inserta una cookie de seguridad para proteger la dirección del controlador de excepciones.  La cookie se comprueba durante el desenredo del marco.  
  
 **\/GS** protege los *parámetros vulnerables* que se pasan en una función.  Un parámetro vulnerable es un puntero, una referencia de C\+\+, una estructura de C \(del tipo POD de C\+\+\) que contiene un puntero o un búfer GS.  
  
 Un parámetro vulnerable se asigna antes que la cookie y las variables locales.  Una saturación del búfer puede sobrescribir estos parámetros.  El código de la función que usa estos parámetros puede provocar un ataque antes de que se devuelva la función y se realice la comprobación de seguridad.  Para reducir este riesgo, el compilador realiza una copia de los parámetros vulnerables durante el prólogo de la función y los coloca bajo el área de almacenamiento de cualquier búfer.  
  
 El compilador no realiza copias de los parámetros vulnerables en las siguientes situaciones:  
  
-   Funciones que no contienen un búfer GS.  
  
-   No se habilitan las optimizaciones \([opciones \/O](../../build/reference/o-options-optimize-code.md)\).  
  
-   Funciones que tienen una lista de argumentos de variable \(...\).  
  
-   Funciones marcadas con [naked](../../cpp/naked-cpp.md).  
  
-   Funciones que contienen código de ensamblado insertado en la primera instrucción.  
  
-   Un parámetro solo se utiliza de manera que sea poco probable que se pueda usar de forma malintencionada en caso de una saturación del búfer.  
  
## Lo que no está protegido  
 La opción del compilador **\/GS** no protege frente a todos los ataques a la seguridad relacionados con la saturación del búfer.  Por ejemplo, si tiene un búfer y vtable en un objeto, la saturación de un búfer podría dañar vtable.  
  
 Incluso si utiliza **\/GS**, intente escribir siempre código seguro que no tenga ninguna saturación de búfer.  
  
#### Para establecer esta opción del compilador en Visual Studio  
  
1.  En el **Explorador de soluciones**, haga clic con el botón secundario del mouse en el proyecto y, a continuación, seleccione **Propiedades**.  
  
     Para obtener más información, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  En el cuadro de diálogo **Páginas de propiedades**, haga clic en la carpeta **C\/C\+\+**.  
  
3.  Haga clic en la página de propiedades **Generación de código**.  
  
4.  Modifique la propiedad **Comprobación de seguridad de búfer**.  
  
#### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BufferSecurityCheck%2A>.  
  
## Ejemplo  
 En este ejemplo se satura un búfer.  Esto produce un error de la aplicación en tiempo de ejecución.  
  
```  
// compile with: /c /W1  
#include <cstring>  
#include <stdlib.h>  
#pragma warning(disable : 4996)   // for strcpy use  
  
// Vulnerable function  
void vulnerable(const char *str) {  
   char buffer[10];  
   strcpy(buffer, str); // overrun buffer !!!  
  
   // use a secure CRT function to help prevent buffer overruns  
   // truncate string to fit a 10 byte buffer  
   // strncpy_s(buffer, _countof(buffer), str, _TRUNCATE);  
}  
  
int main() {  
   // declare buffer that is bigger than expected  
   char large_buffer[] = "This string is longer than 10 characters!!";  
   vulnerable(large_buffer);  
}  
```  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)