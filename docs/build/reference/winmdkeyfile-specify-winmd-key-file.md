---
title: -WINMDKEYFILE (especificar archivo de clave de winmd) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.WINMDKeyFile
dev_langs:
- C++
ms.assetid: 65d88fdc-fff9-49ea-8cfc-b2f408741734
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bc6fa7ff554a15e2d9f13ebfa21e577581ddbad0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="winmdkeyfile-specify-winmd-key-file"></a>/WINMDKEYFILE (especificar archivo de clave winmd)
Especifica una clave o un par de claves para firmar un archivo de metadatos en tiempo de ejecución de Windows (.winmd).  
  
```  
/WINMDKEYFILE:filename  
```  
  
## <a name="remarks"></a>Comentarios  
 Es similar a la [/keyfile](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md) opción del vinculador que se aplica a un archivo .winmd.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Seleccione el **vinculador** carpeta.  
  
3.  Seleccione el **metadatos de Windows** página de propiedades.  
  
4.  En el **archivo de clave de metadatos de Windows** cuadro, escriba la ubicación del archivo.  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)