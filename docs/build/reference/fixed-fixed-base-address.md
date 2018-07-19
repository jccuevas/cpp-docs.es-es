---
title: -FIXED (dirección Base fija) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /fixed
- VC.Project.VCLinkerTool.FixedBaseAddress
dev_langs:
- C++
helpviewer_keywords:
- preferred base address for loading program
- /FIXED linker option
- -FIXED linker option
- FIXED linker option
ms.assetid: 929bba5e-b7d8-40ed-943e-056aa3710fc5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 08b1193b7cfe58aed45e4feec598a49227eafc87
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32374166"
---
# <a name="fixed-fixed-base-address"></a>/FIXED (Dirección base fija)
```  
/FIXED[:NO]  
```  
  
## <a name="remarks"></a>Comentarios  
 Indica al sistema operativo que solo debe cargar el programa en su dirección base preferida. Si dicha dirección base no está disponible, el sistema operativo no cargará el archivo. Para obtener más información, consulte [/BASE (dirección base)](../../build/reference/base-base-address.md).  
  
 /FIXED:NO es el valor predeterminado para un archivo DLL, mientras que /FIXED se utiliza para proyectos de cualquier otro tipo.  
  
 Si se especifica /FIXED, LINK no generará una sección de cambio de ubicación en el programa. En tiempo de ejecución, si el sistema operativo no logra cargar el programa en la dirección especificada, emitirá un mensaje de error y no lo cargará.  
  
 Si se especifica /FIXED:NO, se generará una sección de cambio de ubicación en el programa.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Seleccione el **vinculador** carpeta.  
  
3.  Seleccione el **línea de comandos** página de propiedades.  
  
4.  Escriba el nombre de opción y la configuración el **opciones adicionales** cuadro.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)