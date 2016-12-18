---
title: "/ERRORREPORT (Informar de los errores del compilador) | Microsoft Docs"
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
  - "/ERRORREPORT"
  - "VC.Project.VCLinkerTool.ErrorReporting"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/ERRORREPORT (opción del vinculador)"
  - "ERRORREPORT (opción del vinculador)"
  - "-ERRORREPORT (opción del vinculador)"
ms.assetid: f5fab595-a2f1-4eb0-ab5c-1c0fbd3d8c28
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /ERRORREPORT (Informar de los errores del compilador)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/errorReport:[ none | prompt | queue | send ]  
```  
  
## Comentarios  
 Permite proporcionar directamente a Microsoft la información sobre el error interno del compilador.  
  
 La opción **\/errorReport:send** intenta enviar automáticamente información de error a Microsoft, pero el éxito depende de la configuración del Registro.  Para obtener más información sobre cómo establecer los valores adecuados en el registro, vea [Cómo activar el informe de errores automático en Visual Studio 2008 herramientas de línea de comandos](http://go.microsoft.com/fwlink/?LinkID=184695) en el sitio web de MSDN.  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Haga clic en la carpeta **Propiedades de configuración**.  
  
3.  Haga clic en la carpeta **Vinculador**.  
  
4.  Haga clic en la página de propiedades **Avanzadas**.  
  
5.  Modifique la propiedad **Informes de errores**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ErrorReporting%2A>.  
  
## Vea también  
 [\/errorReport \(Informar de los errores del compilador\)](../../build/reference/errorreport-report-internal-compiler-errors.md)   
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)