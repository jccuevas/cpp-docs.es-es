---
title: -WINMDDELAYSIGN (firmar parcialmente un archivo winmd) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.WINMDDelaySign
dev_langs:
- C++
ms.assetid: 445cd602-62cb-400a-8e3a-4beb6572724d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5c50480fae1f4f3e7421236615d059a642d1074f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32375563"
---
# <a name="winmddelaysign-partially-sign-a-winmd"></a>/WINMDDELAYSIGN (firmar parcialmente un archivo winmd)
Habilita la firma parcial de un archivo de metadatos en tiempo de ejecución de Windows (.winmd) colocando la clave pública en el archivo.  
  
```  
/WINMDDELAYSIGN[:NO]  
```  
  
## <a name="remarks"></a>Comentarios  
 Es similar a la [/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md) opción del vinculador que se aplica el archivo .winmd. Use **/WINMDDELAYSIGN** si desea incluir sólo la clave pública en el archivo .winmd. De forma predeterminada, el vinculador actúa como si **/WINMDDELAYSIGN:NO** se especificaron; es decir, no firma el archivo winmd.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Seleccione el **vinculador** carpeta.  
  
3.  Seleccione el **metadatos de Windows** página de propiedades.  
  
4.  En el **signo de retraso de metadatos de Windows** lista desplegable, seleccione la opción que desee.  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)