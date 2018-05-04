---
title: -IGNOREIDL (Don&#39;t proceso atributos en MIDL) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.IgnoreEmbeddedIDL
- /ignoreidl
dev_langs:
- C++
helpviewer_keywords:
- IGNOREIDL linker option
- -IGNOREIDL linker option
- /IGNOREIDL linker option
ms.assetid: 29514098-6a1c-4317-af2f-1dc268972780
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 14d32be32f019e55f8bad9cc01199d8dc6ae6301
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="ignoreidl-don39t-process-attributes-into-midl"></a>/IGNOREIDL (Don&#39;t proceso atributos en MIDL)
```  
/IGNOREIDL  
```  
  
## <a name="remarks"></a>Comentarios  
 La opción /IGNOREIDL especifica que cualquier [atributos IDL](../../windows/idl-attributes.md) en origen de código no debe procesarse en un archivo IDL.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en el **vinculador** carpeta.  
  
3.  Haga clic en el **IDL incrustado** página de propiedades.  
  
4.  Modificar el **Omitir IDL incrustado** propiedad.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreEmbeddedIDL%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)   
 [/IDLOUT (dar nombre a los archivos de salida MIDL)](../../build/reference/idlout-name-midl-output-files.md)   
 [/TLBOUT (nombre. Archivo TLB)](../../build/reference/tlbout-name-dot-tlb-file.md)   
 [/MIDL (especificar las opciones de línea de comandos MIDL)](../../build/reference/midl-specify-midl-command-line-options.md)   
 [Compilación de programas con atributos](../../windows/building-an-attributed-program.md)