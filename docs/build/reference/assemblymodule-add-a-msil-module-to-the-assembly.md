---
title: "/ASSEMBLYMODULE (Agregar un m&#243;dulo MSIL al ensamblado) | Microsoft Docs"
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
  - "/assemblymodule"
  - "VC.Project.VCLinkerTool.AddModuleNamesToAssembly"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/ASSEMBLYMODULE (opción del vinculador)"
  - "ensamblados [C++]"
  - "ensamblados [C++], agregar módulos"
  - "ASSEMBLYMODULE (opción del vinculador)"
  - "-ASSEMBLYMODULE (opción del vinculador)"
ms.assetid: 67357da8-e4b6-49fd-932c-329a5777f143
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /ASSEMBLYMODULE (Agregar un m&#243;dulo MSIL al ensamblado)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/ASSEMBLYMODULE:filename  
```  
  
## Comentarios  
 donde:  
  
 *filename*  
 Módulo que se desea incluir en el ensamblado.  
  
## Comentarios  
 La opción \/ASSEMBLYMODULE permite agregar una referencia de módulo a un ensamblado.  La información de tipos del módulo no estará disponible para el programa de ensamblado que agregó la referencia de módulo.  Sin embargo, la información de tipos del módulo estará disponible para cualquier programa que haga referencia al ensamblado.  
  
 Se usa [\#using](../../preprocessor/hash-using-directive-cpp.md) tanto para agregar una referencia de módulo a un ensamblado como para poner la información de tipo del módulo a disposición del programa de ensamblado.  
  
 Por ejemplo, considere el siguiente escenario:  
  
1.  Cree un módulo con [\/LN](../../build/reference/ln-create-msil-module.md).  
  
2.  Use \/ASSEMBLYMODULE en otro proyecto para incluir el módulo en la compilación actual, con lo que se creará un ensamblado.  El proyecto no hará referencia al módulo con `#using`.  
  
3.  De este modo, cualquier proyecto que haga referencia al ensamblado podrá usar también tipos del módulo.  
  
 Otras opciones del vinculador que afectan a la generación de ensamblado:  
  
-   [\/ASSEMBLYDEBUG](../../build/reference/assemblydebug-add-debuggableattribute.md)  
  
-   [\/ASSEMBLYLINKRESOURCE](../../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)  
  
-   [\/ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md)  
  
-   [\/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)  
  
-   [\/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)  
  
-   [\/KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)  
  
-   [\/KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)  
  
 El vinculador de Visual C\+\+ acepta archivos .netmodule como entrada y el archivo de salida generado por el vinculador se un ensamblado o un .netmodule sin dependencia en tiempo de ejecución en .netmodules cualquiera de los que se especifican al vinculador.  Para obtener más información, vea [.Archivos netmodule como entrada del vinculador](../../build/reference/netmodule-files-as-linker-input.md).  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Establecer las propiedades de un proyecto de Visual C\+\+](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **Vinculador**.  
  
3.  Haga clic en la página de propiedades **Entrada**.  
  
4.  Modifique la propiedad **Agregar módulo al ensamblado**.  
  
### Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AddModuleNamesToAssembly%2A>.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)