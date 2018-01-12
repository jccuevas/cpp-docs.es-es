---
title: "-RELEASE (espacio de la suma de comprobación) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /release
- VC.Project.VCLinkerTool.SetChecksum
dev_langs: C++
helpviewer_keywords:
- -RELEASE linker option
- /RELEASE linker option
- checksum setting
- RELEASE linker option
ms.assetid: 93bcadf4-29ac-4824-914b-6997e3751d22
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b961c55f04b4f830de30c3d886d9aaee9ef71ea2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="release-set-the-checksum"></a>/RELEASE (Establecer la suma de comprobación)
```  
/RELEASE  
```  
  
## <a name="remarks"></a>Comentarios  
 La opción /RELEASE establece la suma de comprobación en el encabezado de un archivo .exe.  
  
 El sistema operativo requiere la suma de comprobación para controladores de dispositivos. Establece la suma de comprobación para versiones de lanzamiento de los controladores de dispositivos para garantizar su compatibilidad con sistemas operativos futuras.  
  
 La opción /RELEASE se establece de forma predeterminada cuando la [/SUBSYSTEM: Native](../../build/reference/subsystem-specify-subsystem.md) se especifica la opción.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en el **vinculador** carpeta.  
  
3.  Haga clic en el **avanzadas** página de propiedades.  
  
4.  Modificar el **establecer suma de comprobación** propiedad.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SetChecksum%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)