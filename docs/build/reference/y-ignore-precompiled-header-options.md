---
title: "/Y- (Omitir opciones de encabezado precompilado) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/y-"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Y- (opción del compilador) [C++]"
  - "-Y- (opción del compilador) [C++]"
  - "Y- (opción del compilador) [C++]"
ms.assetid: cfaecb36-58db-46b8-b04d-cca6072b1b7a
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# /Y- (Omitir opciones de encabezado precompilado)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Hace que el resto de opciones `/Y` del compilador se omitan \(y no se puede se reemplazar\).  
  
## Sintaxis  
  
```  
/Y-  
```  
  
## Comentarios  
 Para obtener más información acerca de los encabezados precompilados, vea:  
  
-   [\/Y \(Encabezados precompilados\)](../../build/reference/y-precompiled-headers.md)  
  
-   [Crear archivos de encabezado precompilados](../../build/reference/creating-precompiled-header-files.md)  
  
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