---
title: "/DEF (Especificar un archivo de definici&#243;n de m&#243;dulos) | Microsoft Docs"
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
  - "VC.Project.VCLinkerTool.ModuleDefinitionFile"
  - "/def"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/DEF (opción del vinculador)"
  - "DEF (opción del vinculador)"
  - "-DEF (opción del vinculador)"
  - "archivos de definición de módulos"
  - "archivos de definición de módulos, especificar"
ms.assetid: 6497fa68-65f0-48ca-8f66-b87166fc631a
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /DEF (Especificar un archivo de definici&#243;n de m&#243;dulos)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/DEF:filename  
```  
  
## Comentarios  
 donde:  
  
 *filename*  
 Nombre de un archivo de definición de módulos \(.def\) que se va a pasar al vinculador.  
  
## Comentarios  
 La opción \/DEF pasa un archivo de definición de módulo \(.def\) al vinculador.  Solo se puede especificar un archivo .def para LINK.  Para obtener información detallada acerca de los archivos .def, vea [Archivos de definición de módulos](../../build/reference/module-definition-dot-def-files.md).  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Establecer las propiedades de un proyecto de Visual C\+\+](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **Vinculador**.  
  
3.  Haga clic en la página de propiedades **Entrada**.  
  
4.  Modifique la propiedad **Archivo de definición de módulos**.  
  
 Para especificar un archivo .def desde el entorno de desarrollo, agréguelo al proyecto junto con el resto de los archivos y especifíquelo en la opción \/DEF.  
  
### Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ModuleDefinitionFile%2A>.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)