---
title: "/Zs (Solamente comprobaci&#243;n de sintaxis) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/zs"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Zs (opción del compilador) [C++]"
  - "sólo comprobación de sintaxis (opción del compilador)"
  - "Zs (opción del compilador)"
  - "-Zs (opción del compilador) [C++]"
ms.assetid: b4b41e6a-3f41-4d09-9cb6-fde5aa2cfecf
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# /Zs (Solamente comprobaci&#243;n de sintaxis)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta opción indica al compilador que compruebe sólo la sintaxis de los archivos de código fuente en la línea de comandos.  
  
## Sintaxis  
  
```  
/Zs  
```  
  
## Comentarios  
 Cuando se utiliza esta opción, no se crea ningún archivo de salida y los mensajes de error se escriben en la salida estándar.  
  
 La opción **\/Zs** ofrece un método rápido para buscar y corregir errores de sintaxis antes de compilar y vincular un archivo de código fuente.  
  
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