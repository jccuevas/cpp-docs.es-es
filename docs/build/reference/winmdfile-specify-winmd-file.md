---
title: -WINMDFILE (especificar archivo de winmd) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VC.Project.VCLinkerTool.GenerateWindowsMetadataFile
dev_langs: C++
ms.assetid: 062b41b3-14d6-432c-a361-fdb66e918931
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 153e5c0bd42b6fdba59e309483f25f09b86fe9fa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="winmdfile-specify-winmd-file"></a>/WINMDFILE (especificar archivo winmd)
Especifica el nombre de archivo para el archivo de salida de metadatos en tiempo de ejecución de Windows (.winmd) generadas por el [/WINMD](../../build/reference/winmd-generate-windows-metadata.md) opción del vinculador.  
  
```  
/WINMDFILE:filename  
```  
  
## <a name="remarks"></a>Comentarios  
 Use el valor que se especifica en `filename` para invalidar el nombre de archivo de .winmd predeterminado (`binaryname`.winmd). Tenga en cuenta que no se anexa ".winmd" al `filename`.  Si se muestran varios valores en el **/WINMDFILE** línea de comandos, la última de ellas tiene prioridad.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Seleccione el **vinculador** carpeta.  
  
3.  Seleccione el **metadatos de Windows** página de propiedades.  
  
4.  En el **archivo de metadatos de Windows** cuadro, escriba la ubicación del archivo.  
  
## <a name="see-also"></a>Vea también  
 [/WINMD (generar metadatos de Windows)](../../build/reference/winmd-generate-windows-metadata.md)   
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)