---
title: -PDBSTRIPPED (quitar símbolos privados) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /pdbstripped
- VC.Project.VCLinkerTool.StripPrivateSymbols
dev_langs:
- C++
helpviewer_keywords:
- /PDBSTRIPPED linker option
- -PDBSTRIPPED linker option
- .pdb files, stripping private symbols
- PDB files, stripping private symbols
- PDBSTRIPPED linker option
ms.assetid: 9b9e0070-6a13-4142-8180-19c003fbbd55
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 331e490512afe8e9267eb1d0d370cbcf99aa99aa
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32376642"
---
# <a name="pdbstripped-strip-private-symbols"></a>/PDBSTRIPPED (Quitar símbolos privados)
```  
/PDBSTRIPPED:pdb_file_name  
```  
  
## <a name="remarks"></a>Comentarios  
 donde:  
  
 *pdb_file_name*  
 Un nombre especificado por el usuario para la base de datos de programa (PDB) que crea el vinculador.  
  
## <a name="remarks"></a>Comentarios  
 La opción /PDBSTRIPPED crea un segundo archivo de programa (PDB) de la base de datos al generar la imagen del programa con cualquiera del compilador o el vinculador opciones que generan un archivo PDB ([/DEBUG](../../build/reference/debug-generate-debug-info.md), [/Z7](../../build/reference/z7-zi-zi-debug-information-format.md), / Zd, o/Zi). En este segundo archivo PDB se omiten los símbolos que no se desea suministrar a los clientes. El segundo archivo PDB solo contendrá:  
  
-   Símbolos públicos  
  
-   La lista de archivos de objeto y las partes del archivo ejecutable al que contribuyen  
  
-   Registros de depuración de marco puntero optimización (FPO) usa para atravesar la pila  
  
 El archivo PDB no contendrá:  
  
-   Información de tipo  
  
-   Información de número de línea  
  
-   Símbolos de CodeView por objeto archivo como los relativos a las funciones, variables locales y datos estáticos  
  
 El archivo PDB completo se generará cuando se utiliza/PDBSTRIPPED.  
  
 Si no crea un archivo PDB, /PDBSTRIPPED se omite.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en el **vinculador** carpeta.  
  
3.  Haga clic en el **depurar** página de propiedades.  
  
4.  Modificar el **quitar símbolos privados** propiedad.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.StripPrivateSymbols%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)