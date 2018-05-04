---
title: -TLBOUT (nombre. Archivo TLB) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.TypeLibraryFile
- /tlbout
dev_langs:
- C++
helpviewer_keywords:
- tlb files, renaming
- TLBOUT linker option
- /TLBOUT linker option
- .tlb files, renaming
- -TLBOUT linker option
ms.assetid: 0df6d078-2e48-46c9-a1a5-02674d85dce8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1cc4103c387fe7a3dae68b642c10e326b361c54a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="tlbout-name-tlb-file"></a>/TLBOUT (Dar nombre a un archivo .TLB)
```  
/TLBOUT:[path\]filename  
```  
  
## <a name="remarks"></a>Comentarios  
 donde:  
  
 *path*  
 Una especificación de ruta de acceso absoluta o relativa para donde se debe crear el archivo. tlb.  
  
 *filename*  
 Especifica el nombre del archivo .tlb creado por el compilador MIDL. No se supone que ninguna extensión de archivo; Especifique *filename*.tlb si desea que una extensión de tlb.  
  
## <a name="remarks"></a>Comentarios  
 La opción /TLBOUT especifica el nombre y la extensión del archivo TLB.  
  
 El vinculador de Visual C++ llama al compilador MIDL al vincular proyectos que tienen el [módulo](../../windows/module-cpp.md) atributo.  
  
 Si no se especifica TLBOUT, el archivo .tlb obtendrá su nombre de [/IDLOUT](../../build/reference/idlout-name-midl-output-files.md) *filename*. Si no se especifica/IDLOUT, el archivo .tlb llamará vc70.tlb.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en el **vinculador** carpeta.  
  
3.  Haga clic en el **IDL incrustado** página de propiedades.  
  
4.  Modificar el **biblioteca de tipos** propiedad.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación  
  
1.  Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TypeLibraryFile%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)   
 [/IGNOREIDL (no procesar atributos en MIDL)](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)   
 [/MIDL (especificar las opciones de línea de comandos MIDL)](../../build/reference/midl-specify-midl-command-line-options.md)   
 [Compilación de programas con atributos](../../windows/building-an-attributed-program.md)