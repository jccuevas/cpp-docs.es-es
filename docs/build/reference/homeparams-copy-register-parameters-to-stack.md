---
title: "/homeparams (Copiar los par&#225;metros del Registro en la pila) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/homeparams"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/homeparams (opción del compilador) [C++]"
  - "-homeparams (opción del compilador) [C++]"
ms.assetid: 51067de4-24f7-436b-b8d9-bc867a7d53aa
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# /homeparams (Copiar los par&#225;metros del Registro en la pila)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Fuerza la escritura de parámetros pasados en registros en sus ubicaciones en la pila a la entrada de la función.  
  
## Sintaxis  
  
```  
/homeparams  
```  
  
## Comentarios  
 Esta opción del compilador es solo para los compiladores [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] \(compilación nativa y cruzada\)  
  
 Cuando se pasan parámetros en una compilación de [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)], las convenciones de llamada requieren espacio en la pila para los parámetros, incluso para parámetros pasados en registros.  Para obtener más información, vea [Paso de parámetros](../../build/parameter-passing.md).  No obstante, de forma predeterminada, en una versión de lanzamiento, los parámetros de registros no se escribirán en la pila, en el espacio que ya se ha proporcionado para los parámetros.  Esto dificulta la depuración de una compilación optimizada \(versión\) de su programa.  
  
 En una versión de lanzamiento, use **\/homeparams** para asegurarse de que puede depurar la aplicación.  **\/homeparams** implica de hecho una desventaja en cuanto al rendimiento, porque requiere un ciclo para cargar los parámetros de registros en la pila.  
  
 En una versión de depuración, la pila siempre se rellena con parámetros pasados en registros.  
  
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