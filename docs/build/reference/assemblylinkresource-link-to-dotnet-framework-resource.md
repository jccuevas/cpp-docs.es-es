---
title: -ASSEMBLYLINKRESOURCE (vincular a recursos de .NET Framework) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /ASSEMBLYLINKRESOURCE
- VC.Project.VCLinkerTool.AssemblyLinkResource
dev_langs:
- C++
helpviewer_keywords:
- -ASSEMBLYLINKRESOURCE linker option
- ASSEMBLYLINKRESOURCE linker option
- /ASSEMBLYLINKRESOURCE linker option
ms.assetid: 8b6ad184-1b33-47a4-8513-4803cf915b64
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a922ac1a96a59d574f46f7b04db8b160a5079918
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32374055"
---
# <a name="assemblylinkresource-link-to-net-framework-resource"></a>/ASSEMBLYLINKRESOURCE (Vincular a recursos de .NET Framework)
```  
/ASSEMBLYLINKRESOURCE:filename  
```  
  
## <a name="remarks"></a>Comentarios  
 donde:  
  
 *filename*  
 El archivo de recursos de .NET Framework con el que quiere crear un vínculo desde el ensamblado.  
  
## <a name="remarks"></a>Comentarios  
 La opción/ASSEMBLYLINKRESOURCE crea un vínculo a un recurso de .NET Framework en el archivo de salida; el archivo de recursos no se coloca en el archivo de salida. [/ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md) incrusta un archivo de recursos en el archivo de salida.  
  
 Los recursos vinculados son públicos en el ensamblado cuando se crean con el vinculador.  
  
 /ASSEMBLYLINKRESOURCE requiere que el compilador incluya [/CLR](../../build/reference/clr-common-language-runtime-compilation.md); [/LN](../../build/reference/ln-create-msil-module.md) o [/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md) no se permite con/ASSEMBLYLINKRESOURCE.  
  
 Si *filename* es un archivo de recursos de .NET Framework creado, por ejemplo, con [Resgen.exe](/dotnet/framework/tools/resgen-exe-resource-file-generator) o en el entorno de desarrollo, puede tener acceso a los miembros de la **System.Resources** espacio de nombres. Para obtener más información, consulte [System.Resources.ResourceManager](https://msdn.microsoft.com/en-us/library/system.resources.resourcemanager.aspx). Para todos los demás recursos, use el **GetManifestResource** \* métodos en el **System.Reflection.Assembly** clase para acceder al recurso en tiempo de ejecución.  
  
 *nombre de archivo* puede tener cualquier formato de archivo. Por ejemplo, puede que desee realizar una DLL nativa que forme parte del ensamblado, por lo que se puede instalar en la caché Global de ensamblados y accesible desde el código administrado del ensamblado.  
  
 Otras opciones del vinculador que afectan a la generación de ensamblado son:  
  
-   [/ASSEMBLYDEBUG](../../build/reference/assemblydebug-add-debuggableattribute.md)  
  
-   [/ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)  
  
-   [/ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md)  
  
-   [/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)  
  
-   [/KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)  
  
-   [/KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)  
  
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