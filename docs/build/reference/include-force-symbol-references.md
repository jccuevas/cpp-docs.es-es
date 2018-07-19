---
title: -INCLUDE (forzar referencias de símbolos) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /include
- VC.Project.VCLinkerTool.ForceSymbolReferences
dev_langs:
- C++
helpviewer_keywords:
- INCLUDE linker option
- force symbol references linker option
- symbol references linker force
- /INCLUDE linker option
- symbols, add to symbol table
- -INCLUDE linker option
ms.assetid: 4a039677-360a-480f-bd0b-448e239b449c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cfe65344e41b98841c3a4e7bca72b762197510b8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32375654"
---
# <a name="include-force-symbol-references"></a>/INCLUDE (Forzar referencias de símbolos)
```  
/INCLUDE:symbol  
```  
  
## <a name="remarks"></a>Comentarios  
 donde:  
  
 `symbol`  
 Especifica un símbolo que debe agregarse a la tabla de símbolos.  
  
## <a name="remarks"></a>Comentarios  
 La opción /INCLUDE le indica al vinculador para agregar un símbolo especificado a la tabla de símbolos.  
  
 Para especificar varios símbolos, escriba una coma (,), un punto y coma (;) o un espacio entre los nombres de símbolo. En la línea de comandos, especifique/include:`symbol` una vez para cada símbolo.  
  
 El vinculador resuelve `symbol` agregando el objeto que contiene la definición del símbolo para el programa. Esta característica resulta útil para incluir un objeto de biblioteca que de lo contrario no podría vinculado al programa.  
  
 Especificación de un símbolo con esta opción reemplaza la eliminación del símbolo mediante [/OPT: ref](../../build/reference/opt-optimizations.md).  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en el **vinculador** carpeta.  
  
3.  Haga clic en el **entrada** página de propiedades.  
  
4.  Modificar el **forzar referencias de símbolos** propiedad.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ForceSymbolReferences%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)