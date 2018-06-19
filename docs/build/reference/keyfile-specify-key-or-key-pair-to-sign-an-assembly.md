---
title: -KEYFILE (especificar clave o par de claves para firmar un ensamblado) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /keyfile
- VC.Project.VCLinkerTool.KeyFile
dev_langs:
- C++
helpviewer_keywords:
- /KEYFILE linker option
- -KEYFILE linker option
- KEYFILE linker option
ms.assetid: 9b71f8c0-541c-4fe5-a0c7-9364f42ecb06
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 476fd1e49a8c93363f00215d422a79eda808c321
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378826"
---
# <a name="keyfile-specify-key-or-key-pair-to-sign-an-assembly"></a>/KEYFILE (Especificar una clave o par de claves para firmar un ensamblado)
```  
/KEYFILE:filename  
```  
  
## <a name="remarks"></a>Comentarios  
 donde:  
  
 *filename*  
 Archivo que contiene la clave. Escriba la cadena entre comillas dobles ("") si contiene un espacio.  
  
## <a name="remarks"></a>Comentarios  
 El vinculador inserta la clave pública en el manifiesto del ensamblado y firma después el ensamblado final con la clave privada. Para generar un archivo de clave, escriba [sn -k](/dotnet/framework/tools/sn-exe-strong-name-tool) *filename* en la línea de comandos. Se dice que un ensamblado firmado tiene un nombre seguro.  
  
 Si se compila con [/LN](../../build/reference/ln-create-msil-module.md), el nombre del archivo de clave se mantiene en el módulo y se incorpora en el ensamblado que se crea cuando se compila un ensamblado que incluye una referencia explícita al módulo, por medio [#using](../../preprocessor/hash-using-directive-cpp.md), o cuando se vincula con [/ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md).  
  
 También puede pasar la información de cifrado al vinculador con [/keycontainer](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md). Use [/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md) si desea firmar parcialmente un ensamblado. Vea [ensamblados de nombre seguro (firma de ensamblados) (C++ / CLI)](../../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md) para obtener más información sobre cómo firmar un ensamblado.  
  
 En caso de ambos **/keyfile** y **/keycontainer** se especifican (mediante una opción de línea de comandos o mediante un atributo personalizado), el vinculador probará primero el contenedor de claves. Si lo consigue, el ensamblado se firma con la información del contenedor de claves. Si el vinculador no encuentra el contenedor de claves, probará el archivo especificado mediante/keyfile. Si lo consigue, el ensamblado se firma con la información del archivo de clave y la información de la clave se instalará en el contenedor de claves (similar a sn -i) de modo que, en la próxima compilación, el contenedor de claves será válido.  
  
 Tenga en cuenta que un archivo de clave puede contener solo la clave pública.  
  
 Vea [crear y utilizar ensamblados](/dotnet/framework/app-domains/create-and-use-strong-named-assemblies) para obtener más información sobre cómo firmar un ensamblado.  
  
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