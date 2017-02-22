---
title: "/D (Definiciones de preprocesador) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCNMakeTool.PreprocessorDefinitions"
  - "VC.Project.VCCLCompilerTool.PreprocessorDefinitions"
  - "/d"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/D (opción del compilador) [C++]"
  - "constantes, definir"
  - "D (opción del compilador) [C++]"
  - "-D (opción del compilador) [C++]"
  - "macros, compilar"
  - "símbolos de definición del preprocesador"
ms.assetid: b53fdda7-8da1-474f-8811-ba7cdcc66dba
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# /D (Definiciones de preprocesador)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Define un símbolo de preprocesamiento para un archivo de código fuente.  
  
## Sintaxis  
  
```  
/Dname[= | # [{string | number}] ]  
```  
  
## Comentarios  
 Puede usar este símbolo junto con `#if` o `#ifdef` para compilar condicionalmente archivos de código fuente.  La definición del símbolo se mantiene vigente hasta que se vuelve a definir en el código o se anula en el código mediante la directiva `#undef`.  
  
 **\/D** tiene el mismo efecto que la directiva `#define` al principio de un archivo de código fuente, salvo que **\/D** quita las comillas de la línea de comandos y `#define` las mantiene.  
  
 De forma predeterminada, el valor asociado a un símbolo es 1.  Por ejemplo, **\/D**`name` es equivalente a **\/D**`name`**\=1**.  En el ejemplo que encontrará al final de este artículo, se muestra la definición de **TEST** para imprimir `1`.  
  
 Cuando la compilación se realiza con **\/D**`name`**\=**, el símbolo no tiene un valor asociado.  Aunque el símbolo aún se pueda utilizar para compilar código condicionalmente, no se evalúa como ningún valor.  En el ejemplo, si realiza la compilación con **\/DTEST\=**, se produce un error.  Este comportamiento es similar al uso de `#define` con o sin un valor.  
  
 Este comando define el símbolo DEBUG en TEST.c:  
  
 **CL \/DDEBUG  TEST.C**  
  
 Este comando quita todas las apariciones de la palabra clave `__far` en TEST.c:  
  
 **CL \/D\_\_far\=  TEST.C**  
  
 La variable de entorno **CL** no se puede definir en una cadena que contiene el signo igual.  Para usar **\/D** con la variable de entorno **CL**, debe especificar el signo de almohadilla en lugar del signo igual:  
  
```  
SET CL=/DTEST#0  
```  
  
 Al definir un símbolo de preprocesamiento en el símbolo del sistema, tenga en cuenta las reglas de análisis del shell y del compilador.  Por ejemplo, para definir un símbolo de preprocesamiento de signo de porcentaje \(%\) en el programa, especifique dos caracteres de signo de porcentaje \(%%\) en el símbolo del sistema: Si solo especifica uno, se producirá un error en el análisis.  
  
```  
CL /DTEST=%% TEST.C  
```  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  En el panel izquierdo, seleccione **Propiedades de configuración**, **C\/C\+\+** y **Preprocesador**.  
  
3.  En el panel derecho, en la columna derecha de la propiedad de **Definiciones de preprocesador**, abra el menú desplegable y elija **Editar**.  
  
4.  En el cuadro de diálogo **Definiciones de preprocesador**, agregue \(una por línea\), modifique o elimine una o varias definiciones.  Elija **Aceptar** para guardar los cambios.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PreprocessorDefinitions%2A>.  
  
## Ejemplo  
  
```  
// cpp_D_compiler_option.cpp  
// compile with: /DTEST  
#include <stdio.h>  
  
int main( )  
{  
    #ifdef TEST  
        printf_s("TEST defined %d\n", TEST);  
    #else  
        printf_s("TEST not defined\n");  
    #endif  
}  
```  
  
  **TEST defined 1**   
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)   
 [\/U, \/u \(Anular la definición de símbolos\)](../../build/reference/u-u-undefine-symbols.md)   
 [\#undef \(Directiva\)](../../preprocessor/hash-undef-directive-c-cpp.md)   
 [\#define \(Directiva\)](../../preprocessor/hash-define-directive-c-cpp.md)