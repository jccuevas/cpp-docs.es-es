---
title: "/NOASSEMBLY (Crear un m&#243;dulo MSIL) | Microsoft Docs"
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
  - "/NOASSEMBLY"
  - "VC.Project.VCLinkerTool.TurnOffAssemblyGeneration"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/NOASSEMBLY (opción del vinculador)"
  - "ensamblados [C++]"
  - "ensamblados [C++], no se está creando un ensamblado"
  - "NOASSEMBLY (opción del vinculador)"
  - "-NOASSEMBLY (opción del vinculador)"
ms.assetid: 3cea4e70-f451-4395-a626-1930b1b127fe
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /NOASSEMBLY (Crear un m&#243;dulo MSIL)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/NOASSEMBLY  
```  
  
## Comentarios  
 La opción \/NOASSEMBLY indica al vinculador que cree una imagen para el archivo de salida actual sin un ensamblado de .NET Framework.  Un archivo de salida MSIL que no tiene un manifiesto del ensamblado se denomina un módulo.  
  
 De forma predeterminada, se creará un ensamblado,  También puede utilizar la opción del compilador [\/LN \(Crear un módulo MSIL\)](../../build/reference/ln-create-msil-module.md) para crear un módulo.  
  
 Otras opciones del vinculador que afectan a la generación de ensamblado:  
  
-   [\/ASSEMBLYDEBUG](../../build/reference/assemblydebug-add-debuggableattribute.md)  
  
-   [\/ASSEMBLYLINKRESOURCE](../../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)  
  
-   [\/ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)  
  
-   [\/ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md)  
  
-   [\/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)  
  
-   [\/KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)  
  
-   [\/KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Establecer las propiedades de un proyecto de Visual C\+\+](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **Vinculador**.  
  
3.  Haga clic en la página de propiedades **Avanzadas**.  
  
4.  Modifique la propiedad **Desactivar generación de ensamblados**.  
  
### Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TurnOffAssemblyGeneration%2A>.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)