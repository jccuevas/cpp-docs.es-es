---
title: -WINMDKEYCONTAINER (especificar contenedor de claves) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VC.Project.VCLinkerTool.WINMDKEYCONTAINER
dev_langs: C++
ms.assetid: c2fc44dc-7cb5-42b9-897f-1b124928f2f7
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cfb71a932180a41784b9e0894220982a170e6bf2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="winmdkeycontainer-specify-key-container"></a>/WINMDKEYCONTAINER (Especificar contenedor de claves)
Especifica un contenedor de claves para firmar un archivo de metadatos de Windows (.winmd).  
  
```  
/WINMDKEYCONTAINER:name  
```  
  
## <a name="remarks"></a>Comentarios  
 Es similar a la [/keycontainer](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md) opción del vinculador que se aplica a un archivo (.winmd).  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Seleccione el **vinculador** carpeta.  
  
3.  Seleccione el **metadatos de Windows** página de propiedades.  
  
4.  En el **contenedor de claves de metadatos de Windows** cuadro, escriba la ubicación.  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)