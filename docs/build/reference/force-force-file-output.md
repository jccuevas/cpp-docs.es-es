---
title: -FORCE (Forzar resultados de archivo) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.ForceLink
- /force
dev_langs: C++
helpviewer_keywords:
- FORCE linker option
- file output in linker
- /FORCE linker option
- -FORCE linker option
ms.assetid: b1e9a218-a5eb-4e60-a4a4-65b4be15e5da
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8ec19beec52a217df1237de41d0bd81ab447a56d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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