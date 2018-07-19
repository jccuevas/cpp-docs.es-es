---
title: -FORCE (Forzar resultados de archivo) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.ForceLink
- /force
dev_langs:
- C++
helpviewer_keywords:
- FORCE linker option
- file output in linker
- /FORCE linker option
- -FORCE linker option
ms.assetid: b1e9a218-a5eb-4e60-a4a4-65b4be15e5da
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d1daa27ce48590d4a122eafde9f63f7142271610
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32373705"
---
# <a name="force-force-file-output"></a>/FORCE (Forzar resultados de archivo)
```  
/FORCE:[MULTIPLE|UNRESOLVED]  
```  
  
## <a name="remarks"></a>Comentarios  
 La opción /FORCE le indica al vinculador para crear un archivo .exe válido o DLL incluso si se hace referencia a un símbolo pero no definido o definido de forma múltiple.  
  
 La opción/Force puede tomar un argumento opcional:  
  
-   Utilice/Force: Multiple para crear un archivo de salida independientemente de que LINK encuentre más de una definición de un símbolo.  
  
-   / Force: UNRESOLVED se EMPLEA para crear un archivo de salida independientemente de que LINK encuentre un símbolo sin definir. / FORCE: sin resolver se omite si el símbolo de punto de entrada no está resuelto.  
  
 /Force sin argumentos implica tanto definiciones múltiples y sin resolver.  
  
 Un archivo creado con esta opción no funcionen según lo previsto. El vinculador no se vinculará de forma incremental cuando se especifica la opción/Force.  
  
 Si un módulo se compila con **/CLR**, **/FORCE** no creará una imagen.  
  
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