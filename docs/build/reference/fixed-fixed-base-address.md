---
title: "-FIXED (dirección Base fija) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /fixed
- VC.Project.VCLinkerTool.FixedBaseAddress
dev_langs: C++
helpviewer_keywords:
- preferred base address for loading program
- /FIXED linker option
- -FIXED linker option
- FIXED linker option
ms.assetid: 929bba5e-b7d8-40ed-943e-056aa3710fc5
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 201a0357d182713c473fd3e259e4e9c2a71abf4e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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