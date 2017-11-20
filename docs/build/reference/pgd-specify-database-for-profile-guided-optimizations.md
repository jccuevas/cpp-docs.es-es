---
title: -PGD (especificar la base de datos para las optimizaciones guiadas por perfil) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VC.Project.VCLinkerTool.ProfileGuidedDatabase
dev_langs: C++
helpviewer_keywords:
- -PGD linker option
- /PGD linker option
ms.assetid: 9f312498-493b-461f-886f-92652257e443
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 37113ef23adbbb50e36b51ed8ef0035ee20e885e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="pgd-specify-database-for-profile-guided-optimizations"></a>/PGD (Especificar la base de datos para las optimizaciones guiadas por perfiles)
/ PGD:`filename`  
  
## <a name="remarks"></a>Comentarios  
 donde:  
  
 `filename`  
 Especifica el nombre del archivo .pgd que se utilizará para almacenar información sobre el programa en ejecución.  
  
## <a name="remarks"></a>Comentarios  
 Cuando se usa [/LTCG: PGINSTRUMENT](../../build/reference/ltcg-link-time-code-generation.md), use /PGD para especificar un nombre de no predeterminado o ubicación para el archivo. pgd. Si no especifica/pgd, el nombre del archivo .pgd será el mismo que el nombre de archivo salida (.exe o .dll) y se creará en el mismo directorio desde el que se invocó el vínculo.  
  
 Cuando utilice/LTCG: PGOPTIMIZE, use /PGD para especificar el nombre del archivo .pgd que se use para crear la imagen optimizada.  
  
 Para obtener más información, consulte [optimización guiada por perfiles](../../build/reference/profile-guided-optimizations.md).  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Expanda el **propiedades de configuración** nodo.  
  
3.  Expanda el **vinculador** nodo.  
  
4.  Seleccione el **optimización** página de propiedades.  
  
5.  Modificar el **base de datos guiada por perfiles** propiedad.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación  
  
1.  Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ProfileGuidedDatabase%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)