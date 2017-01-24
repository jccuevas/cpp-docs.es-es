---
title: "/KEYFILE (Especificar una clave o par de claves para firmar un ensamblado) | Microsoft Docs"
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
  - "/keyfile"
  - "VC.Project.VCLinkerTool.KeyFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/KEYFILE (opción del vinculador)"
  - "KEYFILE (opción del vinculador)"
  - "-KEYFILE (opción del vinculador)"
ms.assetid: 9b71f8c0-541c-4fe5-a0c7-9364f42ecb06
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /KEYFILE (Especificar una clave o par de claves para firmar un ensamblado)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/KEYFILE:filename  
```  
  
## Comentarios  
 donde:  
  
 *filename*  
 Archivo que contiene la clave.  Si la cadena contiene algún espacio, hay que escribirla entre comillas dobles \(" "\).  
  
## Comentarios  
 El vinculador inserta la clave pública en el manifiesto del ensamblado y firma el ensamblado final con la clave privada.  Para generar un archivo de claves, escriba [sn \-k](../Topic/Sn.exe%20\(Strong%20Name%20Tool\).md) `file` en la línea de comandos.  Se dice que un ensamblado firmado tiene un nombre seguro.  
  
 Si compila con la opción [\/LN](../../build/reference/ln-create-msil-module.md), el nombre del archivo de claves se mantiene en el módulo y se incorpora al ensamblado creado al compilar un ensamblado que incluye una referencia explícita al módulo, por medio de [\#using](../../preprocessor/hash-using-directive-cpp.md), o al vincular con [\/ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md).  
  
 También puede pasar la información de cifrado al vinculador mediante [\/KEYFILE](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md).  Utilice [\/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md) para firmar un ensamblado de forma parcial.  Vea [Ensamblados de nombre seguro \(Firma de ensamblados\)](../../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md) para obtener más información sobre cómo firmar un ensamblado.  
  
 En caso de que se especifiquen **\/KEYFILE** y **\/KEYCONTAINER** \(ya sea mediante una opción de línea de comandos o mediante un atributo personalizado\), el vinculador intentará utilizar primero el contenedor de claves.  Si el intento tiene éxito, el ensamblado se firmará con la información del contenedor de claves.  Si el vinculador no encuentra el contenedor de claves, intentará utilizar el archivo especificado mediante \/KEYFILE.  Si el intento tiene éxito, el ensamblado se firmará con la información contenida en el archivo de claves y la información de claves se instalará en el contenedor de claves \(similar a sn \-i\) de modo que en la siguiente compilación, el contenedor de claves será válido.  
  
 Tenga en cuenta que es posible que un archivo de claves contenga sólo la clave pública.  
  
 Vea [Crear y utilizar ensamblados con nombre seguro](../Topic/Creating%20and%20Using%20Strong-Named%20Assemblies.md) para obtener más información sobre la firma de ensamblados.  
  
 Otras opciones del vinculador que afectan a la generación de ensamblado:  
  
-   [\/ASSEMBLYDEBUG](../../build/reference/assemblydebug-add-debuggableattribute.md)  
  
-   [\/ASSEMBLYLINKRESOURCE](../../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)  
  
-   [\/ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)  
  
-   [\/ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md)  
  
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