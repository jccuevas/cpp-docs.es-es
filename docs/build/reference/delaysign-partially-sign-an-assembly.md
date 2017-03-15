---
title: "/DELAYSIGN (Firmar parcialmente un ensamblado) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/delaysign"
  - "VC.Project.VCLinkerTool.DelaySign"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/DELAYSIGN (opción del vinculador)"
  - "DELAYSIGN (opción del vinculador)"
  - "-DELAYSIGN (opción del vinculador)"
ms.assetid: 15244d30-3ecb-492f-a408-ffe81f38de20
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# /DELAYSIGN (Firmar parcialmente un ensamblado)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/DELAYSIGN[:NO]  
```  
  
## Comentarios  
 where,  
  
 NO  
 Especifica que el ensamblado no debería firmarse parcialmente.  
  
## Comentarios  
 Utilice **\/DELAYSIGN** si sólo desea colocar la clave pública en el ensamblado.  El valor predeterminado es **\/DELAYSIGN:NO**.  
  
 La opción **\/DELAYSIGN** no produce ningún efecto a menos que se utilice con [\/KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md) o [\/KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md).  
  
 Cuando se solicita un ensamblado con firma completa, el compilador calcula el hash del archivo que contiene el manifiesto \(metadatos de ensamblado\) y firma el hash con la clave privada.  La firma digital resultante se almacena en el archivo que contiene el manifiesto.  Cuando se firma un ensamblado de forma retardada, el vinculador no calcula ni almacena la firma, pero reserva espacio en el archivo para poder agregarla más tarde.  
  
 Por ejemplo, si se usa **\/DELAYSIGN**, los comprobadores podrán colocar el ensamblado en la caché global.  Tras la evaluación, se puede firmar completamente el ensamblado colocando la clave privada en el mismo.  
  
 Vea [Ensamblados de nombre seguro \(Firma de ensamblados\)](../../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md) y [Retrasar la firma de un ensamblado](../Topic/Delay%20Signing%20an%20Assembly.md) para obtener más información sobre la forma de firmar un ensamblado.  
  
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