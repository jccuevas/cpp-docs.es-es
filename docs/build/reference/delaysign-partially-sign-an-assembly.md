---
title: -DELAYSIGN (firmar parcialmente un ensamblado) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /delaysign
- VC.Project.VCLinkerTool.DelaySign
dev_langs:
- C++
helpviewer_keywords:
- /DELAYSIGN linker option
- DELAYSIGN linker option
- -DELAYSIGN linker option
ms.assetid: 15244d30-3ecb-492f-a408-ffe81f38de20
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eda1f426f24dd63684fd6831e2efef6838c43a3d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32375069"
---
# <a name="delaysign-partially-sign-an-assembly"></a>/DELAYSIGN (Firmar parcialmente un ensamblado)
```  
/DELAYSIGN[:NO]  
```  
  
## <a name="remarks"></a>Comentarios  
 donde,  
  
 NO  
 Especifica que no se debería firmar parcialmente el ensamblado.  
  
## <a name="remarks"></a>Comentarios  
 Use **/DELAYSIGN** si desea colocar la clave pública del ensamblado. El valor predeterminado es **/delaysign: no**.  
  
 El **/DELAYSIGN** opción no tiene ningún efecto a menos que use con [/keyfile](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md) o [/keycontainer](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md).  
  
 Cuando se solicita un ensamblado totalmente firmado, el compilador genera un valor hash para el archivo que contiene el manifiesto (metadatos del ensamblado) y firma dicho valor mediante la clave privada. La firma digital resultante se almacena en el archivo que contiene el manifiesto. Una vez un ensamblado con firma retrasada, el vinculador no de proceso y se almacena la firma, sino que reserva espacio en el archivo para que la firma se pueda agregar más tarde.  
  
 Por ejemplo, si se usa **/DELAYSIGN** permite a un evaluador colocar el ensamblado en la caché global. Después de realizar pruebas, puede firmar completamente el ensamblado colocando la clave privada en el ensamblado.  
  
 Vea [ensamblados de nombre seguro (firma de ensamblados) (C++ / CLI)](../../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md) y [retrasar la firma de un ensamblado](/dotnet/framework/app-domains/delay-sign-assembly) para obtener más información sobre cómo firmar un ensamblado.  
  
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