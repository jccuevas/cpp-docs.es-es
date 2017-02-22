---
title: "/ASSEMBLYRESOURCE (Incrustar un recurso administrado) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.EmbedManagedResourceFile"
  - "/ASSEMBLYRESOURCE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/ASSEMBLYRESOURCE (opción del vinculador)"
  - "ensamblados [C++]"
  - "ensamblados [C++], vincular archivos de recursos"
  - "ASSEMBLYRESOURCE (opción del vinculador)"
  - "-ASSEMBLYRESOURCE (opción del vinculador)"
ms.assetid: 0ce6e1fb-921b-4b1b-a59c-d35388d789f2
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# /ASSEMBLYRESOURCE (Incrustar un recurso administrado)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/ASSEMBLYRESOURCE:filename[,[name][,PRIVATE]]  
```  
  
## Parámetros  
 *filename*  
 Recurso administrado que se desea incrustar en el ensamblado.  
  
 *name*  
 Opcional.  Nombre lógico del recurso; nombre usado para cargar el recurso.  El valor predeterminado es el nombre del archivo.  
  
 Opcionalmente, puede especificar en el manifiesto del ensamblado si el archivo debe ser privado.  De manera predeterminada, *name* es público en el ensamblado.  
  
## Comentarios  
 La opción \/ASSEMBLYRESOURCE se utiliza para incrustar un recurso en un ensamblado.  
  
 Los recursos creados con el vinculador son públicos en el ensamblado.  El vinculador no permite cambiar el nombre del recurso en el ensamblado.  
  
 Si *filename* es un archivo de recursos \(.resources\) de .NET Framework creado, por ejemplo, por el [Generador de archivos de recursos \(Resgen.exe\)](../Topic/Resgen.exe%20\(Resource%20File%20Generator\).md) o en el entorno de desarrollo, se puede obtener acceso a él con miembros del espacio de nombres **System.Resources** \(vea [System.Resources.ResourceManager](https://msdn.microsoft.com/en-us/library/system.resources.resourcemanager.aspx) si desea obtener más información\).  Para todos los demás recursos, utilice los métodos **GetManifestResource**\* en la clase **System.Reflection.Assembly** para obtener acceso al recurso en tiempo de ejecución.  
  
 Otras opciones del vinculador que afectan a la generación de ensamblado:  
  
-   [\/ASSEMBLYDEBUG](../../build/reference/assemblydebug-add-debuggableattribute.md)  
  
-   [\/ASSEMBLYLINKRESOURCE](../../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)  
  
-   [\/ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)  
  
-   [\/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)  
  
-   [\/KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)  
  
-   [\/KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)  
  
-   [\/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Establecer las propiedades de un proyecto de Visual C\+\+](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **Vinculador**.  
  
3.  Haga clic en la página de propiedades **Entrada**.  
  
4.  Modifique la propiedad **Incrustar un archivo de recursos administrado**.  
  
### Para establecer esta opción del vinculador mediante programación  
  
1.  Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EmbedManagedResourceFile%2A>.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)