---
title: "/WL (Habilitar diagn&#243;sticos de una l&#237;nea) | Microsoft Docs"
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
  - "/wl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/WL (opción del compilador) [C++]"
  - "WL (opción del compilador) [C++]"
  - "-WL (opción del compilador) [C++]"
ms.assetid: 332cadb4-8ea6-45fe-b67d-33ddec1f2c2e
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /WL (Habilitar diagn&#243;sticos de una l&#237;nea)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Anexa información adicional a un mensaje de error o de advertencia.  
  
## Sintaxis  
  
```  
/WL  
```  
  
## Comentarios  
 Los mensajes de error y de advertencia del compilador de C\+\+ pueden ir acompañados de otra información que, de forma predeterminada, aparece en una línea nueva.  Si compila desde la línea de comandos, la línea de información adicional puede estar anexa al mensaje de error o de advertencia.  Esto podría resultarle útil si captura el resultado de la compilación en un archivo de registro y después lo procesa para buscar todos los errores y advertencias.  Un signo de punto y coma separa el mensaje de error o de advertencia de la línea adicional.  
  
 No todos los mensajes de error y de advertencia tienen una línea de información adicional.  El siguiente código genera un error que tiene una línea adicional de información; le permite comprobar el efecto del uso de **\/WL**.  
  
```  
// compiler_option_WL.cpp  
// compile with: /WL  
#include <queue>  
int main() {  
   std::queue<int> q;  
   q.fromthecontinuum();   // C2039  
}  
```  
  
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