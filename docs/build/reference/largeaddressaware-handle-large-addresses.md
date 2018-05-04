---
title: -LARGEADDRESSAWARE (procesar direcciones largas) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.LargeAddressAware
- /largeaddressaware
dev_langs:
- C++
helpviewer_keywords:
- LARGEADDRESSAWARE linker option
- -LARGEADDRESSAWARE linker option
- /LARGEADDRESSAWARE linker option
ms.assetid: a29756c8-e893-47a9-9750-1f0d25359385
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4f81424c49c5d67713cf478f69701c52504cfa8c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="largeaddressaware-handle-large-addresses"></a>/LARGEADDRESSAWARE (Procesar direcciones largas)
```  
/LARGEADDRESSAWARE[:NO]  
```  
  
## <a name="remarks"></a>Comentarios  
 La opción /LARGEADDRESSAWARE indica al vinculador que la aplicación puede controlar direcciones mayores de 2 gigabytes. En los compiladores de 64 bits, esta opción está habilitada de forma predeterminada. En los compiladores de 32 bits, / LARGEADDRESSAWARE: no está habilitado si /LARGEADDRESSAWARE no se especifica lo contrario en la línea del vinculador.  
  
 Si se vincula una aplicación por medio de/LARGEADDRESSAWARE, DUMPBIN [/HEADERS](../../build/reference/headers.md) mostrará información al respecto.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en el **vinculador** carpeta.  
  
3.  Haga clic en el **System** página de propiedades.  
  
4.  Modificar el **habilitar direcciones largas** propiedad.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LargeAddressAware%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)