---
title: -ASSEMBLYDEBUG (Agregar DebuggableAttribute) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.AssemblyDebug
- /ASSEMBLYDEBUG
dev_langs: C++
helpviewer_keywords:
- /ASSEMBLYDEBUG linker option
- -ASSEMBLYDEBUG linker option
- ASSEMBLYDEBUG linker option
ms.assetid: 94443af3-470c-41d7-83a0-7434563d7982
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 80b4759b5594096b3a599d6e3324bfeaab0376a7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="assemblydebug-add-debuggableattribute"></a>/ASSEMBLYDEBUG (Agregar DebuggableAttribute)
```  
/ASSEMBLYDEBUG[:DISABLE]  
```  
  
 /ASSEMBLYDEBUG emite el **DebuggableAttribute** atributo con optimizaciones de JIT seguimiento y se deshabilita la información de depuración. Esto es lo mismo que especificar el siguiente atributo de origen:  
  
```  
[assembly:Debuggable(true, true)];   // same as /ASSEMBLYDEBUG  
```  
  
 / ASSEMBLYDEBUG: DISABLE emite el **DebuggableAttribute** atributo pero deshabilita el seguimiento de información de depuración y habilita las optimizaciones JIT. Esto es lo mismo que especificar el siguiente atributo de origen:  
  
```  
[assembly:Debuggable(false, false)];   // same as /ASSEMBLYDEBUG:DISABLE  
```  
  
 El valor predeterminado es no emitir el **DebuggableAttribute** atributo.  
  
 DebuggableAttribute también puede agregarse a un ensamblado directamente en el código fuente. Por ejemplo,  
  
```  
[assembly:Debuggable(true, true)];   // same as /ASSEMBLYDEBUG  
```  
  
## <a name="remarks"></a>Comentarios  
 Es necesario especificar explícitamente que una imagen administrada sea depurable. Usar [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) por sí solo no es suficiente.  
  
 Otras opciones del vinculador que afectan a la generación de ensamblado son:  
  
-   [/ASSEMBLYLINKRESOURCE](../../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)  
  
-   [/ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)  
  
-   [/ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md)  
  
-   [/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)  
  
-   [/KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)  
  
-   [/KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)  
  
-   [/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en el **vinculador** carpeta.  
  
3.  Haga clic en el **depurar** página de propiedades.  
  
4.  Modificar el **ensamblado depurable** propiedad.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AssemblyDebug%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)