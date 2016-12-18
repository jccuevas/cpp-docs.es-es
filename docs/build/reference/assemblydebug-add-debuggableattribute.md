---
title: "/ASSEMBLYDEBUG (Agregar DebuggableAttribute) | Microsoft Docs"
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
  - "VC.Project.VCLinkerTool.AssemblyDebug"
  - "/ASSEMBLYDEBUG"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/ASSEMBLYDEBUG (opción del vinculador)"
  - "ASSEMBLYDEBUG (opción del vinculador)"
  - "-ASSEMBLYDEBUG (opción del vinculador)"
ms.assetid: 94443af3-470c-41d7-83a0-7434563d7982
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /ASSEMBLYDEBUG (Agregar DebuggableAttribute)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/ASSEMBLYDEBUG[:DISABLE]  
```  
  
 \/ASSEMBLYDEBUG emite el atributo **DebuggableAttribute** con seguimiento de la información de depuración y deshabilita las optimizaciones JIT.  El resultado es el mismo que el de especificar el siguiente atributo en el código fuente:  
  
```  
[assembly:Debuggable(true, true)];   // same as /ASSEMBLYDEBUG  
```  
  
 \/ASSEMBLYDEBUG:DISABLE emite el atributo **DebuggableAttribute** pero deshabilita el seguimiento de la información de depuración y habilita las optimizaciones JIT.  El resultado es el mismo que el de especificar el siguiente atributo en el código fuente:  
  
```  
[assembly:Debuggable(false, false)];   // same as /ASSEMBLYDEBUG:DISABLE  
```  
  
 El comportamiento predeterminado es no emitir el atributo **DebuggableAttribute**.  
  
 El atributo Debuggable también se puede agregar a un ensamblado directamente en el código fuente.  Por ejemplo,  
  
```  
[assembly:Debuggable(true, true)];   // same as /ASSEMBLYDEBUG  
```  
  
## Comentarios  
 En Visual C\+\+ .NET 2003 y versiones posteriores, es necesario especificar explícitamente el hecho de que una imagen administrada se pueda depurar.  El uso de sólo [\/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) no es suficiente.  
  
 Otras opciones del vinculador que afectan a la generación de ensamblado:  
  
-   [\/ASSEMBLYLINKRESOURCE](../../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)  
  
-   [\/ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)  
  
-   [\/ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md)  
  
-   [\/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)  
  
-   [\/KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)  
  
-   [\/KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)  
  
-   [\/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Establecer las propiedades de un proyecto de Visual C\+\+](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **Vinculador**.  
  
3.  Haga clic en la página de propiedades **Depurar**.  
  
4.  Modifique la propiedad **Ensamblado depurable**.  
  
### Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AssemblyDebug%2A>.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)