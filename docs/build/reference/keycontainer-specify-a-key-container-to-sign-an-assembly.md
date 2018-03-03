---
title: -KEYCONTAINER (especificar un contenedor de claves para firmar un ensamblado) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.KeyContainer
- /keycontainer
dev_langs:
- C++
helpviewer_keywords:
- KEYCONTAINER linker option
- /KEYCONTAINER linker option
- -KEYCONTAINER linker option
ms.assetid: 94882d12-b77a-49c7-96d0-18a31aee001e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f0e1f31e85c23b32bee1b8b968bbec65ee82beb9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="keycontainer-specify-a-key-container-to-sign-an-assembly"></a>/KEYCONTAINER (Especificar un contenedor de claves para firmar un ensamblado)
```  
/KEYCONTAINER:name  
```  
  
## <a name="remarks"></a>Comentarios  
 donde,  
  
 *name*  
 Contenedor que contiene la clave. Escriba la cadena entre comillas dobles ("") si contiene un espacio.  
  
## <a name="remarks"></a>Comentarios  
 El vinculador crea un ensamblado firmado insertando una clave pública en el manifiesto del ensamblado y firma el ensamblado final con la clave privada. Para generar un archivo de clave, escriba [sn -k](/dotnet/framework/tools/sn-exe-strong-name-tool) *filename* en la línea de comandos. **sn -i** instala el par de claves en un contenedor.  
  
 Si se compila con [/LN](../../build/reference/ln-create-msil-module.md), el nombre del archivo de clave se mantiene en el módulo y se incorpora en el ensamblado que se crea cuando se compila un ensamblado que incluye una referencia explícita al módulo, por medio [#using](../../preprocessor/hash-using-directive-cpp.md), o cuando se vincula con [/ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md).  
  
 También puede pasar la información de cifrado al compilador con [/keyfile](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md). Use [/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md) si desea firmar parcialmente un ensamblado. Vea [ensamblados de nombre seguro (firma de ensamblados) (C++ / CLI)](../../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md) para obtener más información sobre cómo firmar un ensamblado.  
  
 Otras opciones del vinculador que afectan a la generación de ensamblado son:  
  
-   [/ASSEMBLYDEBUG](../../build/reference/assemblydebug-add-debuggableattribute.md)  
  
-   [/ASSEMBLYLINKRESOURCE](../../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)  
  
-   [/ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)  
  
-   [/ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md)  
  
-   [/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en el **vinculador** carpeta.  
  
3.  Haga clic en la página de propiedades **Línea de comandos** .  
  
4.  Escriba la opción en la **opciones adicionales** cuadro.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)