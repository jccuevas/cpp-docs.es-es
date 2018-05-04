---
title: -NOLOGO (suprimir el titular de inicio) (vinculador) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.SuppressStartupBanner
- /nologo
dev_langs:
- C++
helpviewer_keywords:
- suppress startup banner linker option
- -NOLOGO linker option
- /NOLOGO linker option
- copyright message
- version numbers, preventing linker display
- banners, suppressing startup
- NOLOGO linker option
ms.assetid: 3b20dddd-eca6-4545-a331-9f70bf720197
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a76e99496114c0ebdc60f81724e67dd88a482055
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="nologo-suppress-startup-banner-linker"></a>/NOLOGO (Suprimir el titular de inicio) (Vinculador)
```  
/NOLOGO  
```  
  
## <a name="remarks"></a>Comentarios  
 La opción/nologo evita que la visualización del número de versión y de mensaje de copyright.  
  
 Esta opción también suprime la repetición de archivos de comandos. Para obtener más información, consulte [archivos de comandos LINK](../../build/reference/link-command-files.md).  
  
 De forma predeterminada, esta información se envía mediante el enlazador para la ventana de salida. En la línea de comandos que se envía a la salida estándar y puede redirigirse a un archivo.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Esta opción solo debe utilizarse desde la línea de comandos.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación  
  
1.  Esta opción del vinculador no se puede cambiar mediante programación.  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)