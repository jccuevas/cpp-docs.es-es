---
title: "-ALIGN (alineación de sección) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.Alignment
- /align
dev_langs: C++
helpviewer_keywords:
- sections, specifying alignment
- ALIGN linker option
- /ALIGN linker option
- -ALIGN linker option
- section alignment
- sections
ms.assetid: f2f8ac24-e90e-4bea-8205-f2960a3b1740
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e620719d5a69c333a45664fba5967a740224d4d5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="align-section-alignment"></a>/ALIGN (Alineación de sección)
```  
/ALIGN[:number]  
```  
  
## <a name="remarks"></a>Comentarios  
 donde:  
  
 `number`  
 El valor de alineación.  
  
## <a name="remarks"></a>Comentarios  
 La opción /ALIGN especifica la alineación de cada sección en el espacio de direcciones lineales del programa. El `number` argumento está en bytes y debe ser una potencia de dos. El valor predeterminado es 4K (4096). El vinculador emite una advertencia si la alineación produce una imagen no válida.  
  
 A menos que se está escribiendo una aplicación como un controlador de dispositivo, no es necesario modificar la alineación.  
  
 Es posible modificar la alineación de una sección determinada con el parámetro de alinear a la [/SECTION](../../build/reference/section-specify-section-attributes.md) opción.  
  
 El valor de alineación especificado no puede ser menor que la alineación de sección más grande.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en el **vinculador** carpeta.  
  
3.  Haga clic en la página de propiedades **Línea de comandos** .  
  
4.  Escriba la opción en la **opciones adicionales** cuadro.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)