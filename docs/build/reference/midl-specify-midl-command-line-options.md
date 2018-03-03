---
title: "-MIDL (especificar las opciones de línea de comandos MIDL) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /midl
- VC.Project.VCLinkerTool.MidlCommandFile
dev_langs:
- C++
helpviewer_keywords:
- -MIDL linker option
- MIDL
- /MIDL linker option
- MIDL linker option
- MIDL, command line options
ms.assetid: 22dc259e-b34c-4ed3-a380-4beb734482c1
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f8e842f4cf0f9c52945c04739879d0132eb34171
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="midl-specify-midl-command-line-options"></a>/MIDL (Especificar las opciones de la línea de comandos de MIDL)
```  
/MIDL:@file  
```  
  
## <a name="remarks"></a>Comentarios  
 donde:  
  
 `file`  
 El nombre del archivo que contiene [opciones de línea de comandos MIDL](http://msdn.microsoft.com/library/windows/desktop/aa366839).  
  
## <a name="remarks"></a>Comentarios  
 Todas las opciones para la conversión de un archivo IDL en archivo TLB deben indicarse `file`; Opciones de línea de comandos de MIDL no se puede especificar en la línea de comandos del vinculador. Si no se especifica /MIDL, se invocará el compilador MIDL con solo el nombre del archivo IDL y no hay otras opciones.  
  
 El archivo debe contener una opción de línea de comandos de MIDL por línea.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en el **vinculador** carpeta.  
  
3.  Haga clic en el **IDL incrustado** página de propiedades.  
  
4.  Modificar el **comandos MIDL** propiedad.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MidlCommandFile%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)   
 [/IDLOUT (dar nombre a los archivos de salida MIDL)](../../build/reference/idlout-name-midl-output-files.md)   
 [/IGNOREIDL (no procesar atributos en MIDL)](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)   
 [/TLBOUT (nombre. Archivo TLB)](../../build/reference/tlbout-name-dot-tlb-file.md)   
 [Compilación de programas con atributos](../../windows/building-an-attributed-program.md)