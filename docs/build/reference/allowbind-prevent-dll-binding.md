---
title: "/ALLOWBIND (Evitar el enlace de archivos DLL) | Microsoft Docs"
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
  - "VC.Project.VCLinkerTool.PreventDLLBinding"
  - "/allowbind"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/ALLOWBIND (opción del vinculador)"
  - "ALLOWBIND (opción del vinculador)"
  - "-ALLOWBIND (opción del vinculador)"
  - "enlazar archivos DLL"
  - "DLL [C++], impedir el enlace"
  - "impedir el enlace DLL"
ms.assetid: 30e37e24-12e4-407e-988a-39d357403598
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /ALLOWBIND (Evitar el enlace de archivos DLL)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/ALLOWBIND[:NO]  
```  
  
## Comentarios  
 \/ALLOWBIND:NO establece en el encabezado de una DLL un bit que le indica a Bind.exe que la imagen no se puede enlazar.  Puede que quiera evitar que una DLL se enlace si se firmó digitalmente \(el enlace invalida la firma\).  
  
 Puede editar la funcionalidad \/ALLOWBIND de una DLL existente con la opción [\/ALLOWBIND](../../build/reference/allowbind.md) de la utilidad EDITBIN.  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Expanda **Propiedades de configuración** y **Vinculador** y seleccione **Línea de comandos**.  
  
3.  Introduzca `/ALLOWBIND:NO` en **Opciones adicionales**.  
  
### Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)   
 [Función BindImage](http://msdn.microsoft.com/library/windows/desktop/ms679278.aspx)   
 [Función BindImageEx](http://msdn.microsoft.com/library/windows/desktop/ms679279.aspx)