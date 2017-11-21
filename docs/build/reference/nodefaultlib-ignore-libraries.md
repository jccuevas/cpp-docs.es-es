---
title: -NODEFAULTLIB (Omitir bibliotecas) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.OVERWRITEAllDefaultLibraries
- VC.Project.VCLinkerTool.OVERWRITEDefaultLibraryNames
- /nodefaultlib
dev_langs: C++
helpviewer_keywords:
- default libraries, removing
- -NODEFAULTLIB linker option
- libraries, ignore
- NODEFAULTLIB linker option
- /NODEFAULTLIB linker option
- ignore libraries linker option
ms.assetid: 7270b673-6711-468e-97a7-c2925ac2be6e
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1172bc3dbed6353e31e34a0f406d2ea688ce78c2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="nodefaultlib-ignore-libraries"></a>/NODEFAULTLIB (Omitir bibliotecas)
```  
/NODEFAULTLIB[:library]   
```  
  
## <a name="remarks"></a>Comentarios  
 donde:  
  
 *biblioteca de*  
 Una biblioteca que desea que el vinculador para pasar por alto cuando resuelve referencias externas.  
  
## <a name="remarks"></a>Comentarios  
 La opción /NODEFAULTLIB le indica al vinculador que quite una o más bibliotecas predeterminadas de la lista de bibliotecas que se busca al resolver referencias externas.  
  
 Para crear un archivo .obj que no contiene referencias a bibliotecas predeterminadas, use [/Zl (omitir nombres de biblioteca predeterminada)](../../build/reference/zl-omit-default-library-name.md).  
  
 De forma predeterminada, esta opción quitará todas las bibliotecas predeterminadas de la lista de bibliotecas que se busca al resolver referencias externas. Opcional *biblioteca* parámetro permite quitar una biblioteca especificada o bibliotecas de la lista de bibliotecas que se busca al resolver referencias externas. Especificar una opción / NODEFAULTLIB para cada biblioteca que desea excluir.  
  
 El vinculador resuelve las referencias a definiciones externas buscando en primer lugar en las bibliotecas que se especifiquen explícitamente, a continuación, en las bibliotecas especificadas con la opción /DEFAULTLIB y, a continuación, en las bibliotecas predeterminadas mencionadas en los archivos .obj.  
  
 / NODEFAULTLIB:*biblioteca* invalida [a/DEFAULTLIB:](../../build/reference/defaultlib-specify-default-library.md)*biblioteca* cuando el mismo *biblioteca* nombre se especifica en ambos.  
  
 Si utiliza/NODEFAULTLIB, por ejemplo, para generar un programa sin la biblioteca de tiempo de ejecución de C, tendrá que usar [/Entry](../../build/reference/entry-entry-point-symbol.md) para especificar el punto de entrada (función) en el programa. Para obtener más información, vea [Características de la biblioteca CRT](../../c-runtime-library/crt-library-features.md).  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en el **vinculador** carpeta.  
  
3.  Haga clic en el **entrada**página de propiedades.  
  
4.  Seleccione el **omitir todas las bibliotecas predeterminadas** propiedad o especificar una lista de las bibliotecas que desea omitir en la **Omitir biblioteca específica** propiedad. El **línea de comandos** página de propiedades mostrará el efecto de los cambios que realice para estas propiedades.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreDefaultLibraryNames%2A> y <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreAllDefaultLibraries%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)