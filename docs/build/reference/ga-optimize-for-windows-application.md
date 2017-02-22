---
title: "/GA (optimizar c&#243;digo para una aplicaci&#243;n para Windows) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLCompilerTool.OptimizeForWindowsApplication"
  - "/ga"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/GA (opción del compilador) [C++]"
  - "GA (opción del compilador) [C++]"
  - "-GA (opción del compilador) [C++]"
  - "Optimizar para Windows (opciones del compilador)"
ms.assetid: be97323e-15a0-4836-862c-95980b51926a
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# /GA (optimizar c&#243;digo para una aplicaci&#243;n para Windows)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Produce un código más eficiente para que un archivo .exe tenga acceso a las variables de almacenamiento local de subprocesos \(TLS\).  
  
## Sintaxis  
  
```  
/GA  
```  
  
## Comentarios  
 **\/GA** acelera el acceso a los datos declarados con [\_\_declspec\(thread\)](../../cpp/declspec.md) en un programa basado en Windows.  Cuando esta opción está establecida, se supone que la macro [\_\_tls\_index](http://msdn.microsoft.com/library/windows/desktop/ms686749) es 0.  
  
 El uso de **\/GA** para un archivo DLL puede causar la generación de un código incorrecto.  
  
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