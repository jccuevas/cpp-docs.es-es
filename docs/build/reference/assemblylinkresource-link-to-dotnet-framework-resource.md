---
title: "/ASSEMBLYLINKRESOURCE (Vincular a recursos de .NET Framework) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/ASSEMBLYLINKRESOURCE"
  - "VC.Project.VCLinkerTool.AssemblyLinkResource"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/ASSEMBLYLINKRESOURCE (opción del vinculador)"
  - "ASSEMBLYLINKRESOURCE (opción del vinculador)"
  - "-ASSEMBLYLINKRESOURCE (opción del vinculador)"
ms.assetid: 8b6ad184-1b33-47a4-8513-4803cf915b64
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /ASSEMBLYLINKRESOURCE (Vincular a recursos de .NET Framework)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/ASSEMBLYLINKRESOURCE:filename  
```  
  
## Comentarios  
 donde:  
  
 *filename*  
 Archivo de recursos de .NET Framework con el que desea crear un vínculo desde el ensamblado.  
  
## Comentarios  
 La opción \/ASSEMBLYLINKRESOURCE crea un vínculo a un recurso de .NET Framework en el archivo de salida; el archivo de recursos no se coloca en el archivo de salida.  [\/ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md), en cambio, incrusta un archivo de recursos en el archivo de salida.  
  
 Los recursos vinculados creados con el vinculador son públicos en el ensamblado.  
  
 \/ASSEMBLYLINKRESOURCE requiere que el compilador incluya [\/clr](../../build/reference/clr-common-language-runtime-compilation.md); [\/LN](../../build/reference/ln-create-msil-module.md) o [\/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md) no se permite con \/ASSEMBLYLINKRESOURCE.  
  
 Si *filename* es un archivo de recursos de .NET Framework creado, por ejemplo, con [Resgen.exe](../Topic/Resgen.exe%20\(Resource%20File%20Generator\).md) o en el entorno de desarrollo, se puede obtener acceso a él con miembros del espacio de nombres **System.Resources**.  Para obtener más información, vea [System.Resources.ResourceManager](https://msdn.microsoft.com/en-us/library/system.resources.resourcemanager.aspx).  Para todos los demás recursos, utilice los métodos **GetManifestResource**\* de la clase **System.Reflection.Assembly** para tener acceso al recurso en tiempo de ejecución.  
  
 *filename* puede tener cualquier formato de archivo.  Por ejemplo, se puede hacer que una DLL nativa forme parte de un ensamblado para que se pueda instalar en la caché global de ensamblados y sea accesible desde código administrado del ensamblado.  
  
 Otras opciones del vinculador que afectan a la generación de ensamblado:  
  
-   [\/ASSEMBLYDEBUG](../../build/reference/assemblydebug-add-debuggableattribute.md)  
  
-   [\/ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)  
  
-   [\/ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md)  
  
-   [\/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)  
  
-   [\/KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)  
  
-   [\/KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)  
  
-   [\/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Establecer las propiedades de un proyecto de Visual C\+\+](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **Vinculador**.  
  
3.  Haga clic en la página de propiedades **Línea de comandos**.  
  
4.  Escriba la opción en el cuadro **Opciones adicionales**.  
  
### Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)