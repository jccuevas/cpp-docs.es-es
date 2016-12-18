---
title: "/H (Restringir la longitud de los nombres externos) | Microsoft Docs"
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
  - "/h"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/H (opción del compilador) [C++]"
  - "nombres externos"
  - "H (opción del compilador) [C++]"
  - "-H (opción del compilador) [C++]"
  - "longitud del nombre público"
ms.assetid: de701dd3-ed04-4c88-8195-960d2520ec2e
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /H (Restringir la longitud de los nombres externos)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Restringe la longitud de los nombres externos  
  
## Sintaxis  
  
```  
/Hnumber  
```  
  
## Argumentos  
 `number`  
 Especifica la longitud máxima permitida para los nombres externos en un programa.  
  
## Comentarios  
 De forma predeterminada, la longitud de los nombres externos \(públicos\) es de 2.047 caracteres.  Esto ocurre tanto en C como en C\+\+.  El uso de **\/H** sólo puede disminuir la longitud máxima permitida para los identificadores, no aumentarla.  Un espacio entre **\/H** y `number` es opcional.  
  
 Si un programa contiene nombres externos más largos que `number`, los caracteres adicionales se omiten.  Si compila un programa sin **\/H** y un identificador contiene más de 2.047 caracteres, el compilador generará [Error irrecuperable C1064](../../error-messages/compiler-errors-1/fatal-error-c1064.md).  
  
 En el límite de longitud se incluye cualquier signo inicial de subrayado \(\_\) o signo de arroba \(@\) creado por el compilador.  Estos caracteres forman parte del identificador y ocupan una ubicación significativa.  
  
-   El compilador agrega un carácter de subrayado inicial \(\_\) a los nombres modificados por las convenciones de llamadas `__cdecl` \(valor predeterminado\) y `__stdcall`, y un signo de arroba inicial \(@\) a los nombres modificados por la convención de llamadas `__fastcall`.  
  
-   El compilador anexa información de tamaño de los argumentos a los nombres modificados por las convenciones de llamadas `__fastcall` y `__stdcall`, y agrega información de tipo a los nombres de C\+\+.  
  
 Encontrará **\/H** útil:  
  
-   Si crea programas en varios idiomas o programas portables.  
  
-   Si usa herramientas que imponen límites a la longitud de los identificadores externos.  
  
-   Si desea restringir el espacio que usan los símbolos en una versión de depuración.  
  
 En el ejemplo siguiente se muestra cómo el uso de **\/H** puede causar errores si se limita demasiado la longitud de los identificadores:  
  
```  
// compiler_option_H.cpp  
// compile with: /H5  
// processor: x86  
// LNK2005 expected  
void func1(void);  
void func2(void);  
  
int main() { func1(); }  
  
void func1(void) {}  
void func2(void) {}  
```  
  
 También debe tener cuidado, cuando use la opción **\/H**, con los identificadores de compilador predefinidos.  Si la longitud máxima de los identificadores es demasiado pequeña, algunos identificadores predefinidos no se resolverán, lo mismo que determinadas llamadas a funciones de biblioteca.  Por ejemplo, si se utiliza la función `printf` y se especifica la opción **\/H5** en tiempo de compilación, se creará el símbolo **\_prin** para hacer referencia a `printf` y ésta no se encontrará en la biblioteca.  
  
 El uso de **\/H** es incompatible con [\/GL \(Optimización de todo el programa\)](../../build/reference/gl-whole-program-optimization.md).  
  
 La opción **\/H** ha quedado desusada; se han aumentado los límites de longitud máximos y ya no se necesita **\/H**.  Para obtener más información, vea [Deprecated Compiler Options in Visual C\+\+ 2005](http://msdn.microsoft.com/es-es/aa59fce3-50b8-4f66-9aeb-ce09a7a84cce).  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Haga clic en la carpeta **C\/C\+\+**.  
  
3.  Haga clic en la página de propiedades **Línea de comandos**.  
  
4.  Escriba la opción del compilador en el cuadro **Opciones adicionales**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)