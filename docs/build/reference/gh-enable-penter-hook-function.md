---
title: "/GH (Habilitar la funci&#243;n de enlace _penter) | Microsoft Docs"
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
  - "_penter"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Gh (opción del compilador) [C++]"
  - "_penter (función)"
  - "Gh (opción del compilador) [C++]"
  - "-Gh (opción del compilador) [C++]"
ms.assetid: 1510a082-8a0e-486e-a309-6add814b494f
caps.latest.revision: 18
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /GH (Habilitar la funci&#243;n de enlace _penter)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Provoca una llamada a la función `_penter` al principio de cada método o función.  
  
## Sintaxis  
  
```  
/Gh  
```  
  
## Comentarios  
 La función `_penter` no forma parte de ninguna biblioteca y se deja a criterio del programador proporcionar una definición para `_penter`.  
  
 Salvo que tenga intención de llamar explícitamente a `_penter`, no será necesario que proporcione un prototipo.  La función debe parecer como si tuviera el siguiente prototipo, y debe insertar el contenido de todos los registros al entrar y extraer el contenido sin modificar al salir:  
  
```  
void __declspec(naked) _cdecl _penter( void );  
```  
  
 Esta declaración no está disponible para los proyectos de 64 bits.  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Haga clic en la carpeta **C\/C\+\+**.  
  
3.  Haga clic en la página de propiedades **Línea de comandos**.  
  
4.  Escriba la opción del compilador en el cuadro **Opciones adicionales**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## Ejemplo  
 El código que se muestra a continuación, si se compila con **\/Gh**, muestra cómo se llama dos veces a `_penter`; una vez al escribir la función `main` y otra al escribir la función `x`.  
  
```  
// Gh_compiler_option.cpp  
// compile with: /Gh  
// processor: x86  
#include <stdio.h>  
void x() {}  
  
int main() {  
   x();  
}  
  
extern "C" void __declspec(naked) _cdecl _penter( void ) {  
   _asm {  
      push eax  
      push ebx  
      push ecx  
      push edx  
      push ebp  
      push edi  
      push esi  
    }  
  
   printf_s("\nIn a function!");  
  
   _asm {  
      pop esi  
      pop edi  
      pop ebp  
      pop edx  
      pop ecx  
      pop ebx  
      pop eax  
      ret  
    }  
}  
```  
  
  **¡En una función\!**  
**¡En una función\!**   
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)