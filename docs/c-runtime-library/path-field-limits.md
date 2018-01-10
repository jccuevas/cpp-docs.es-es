---
title: "Límites del campo de ruta de acceso | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _MAX_EXT
- _MAX_DIR
- _MAX_PATH
- _MAX_FNAME
- _MAX_DRIVE
dev_langs: C++
helpviewer_keywords:
- path field constants
- MAX_FNAME constant
- _MAX_DIR constant
- _MAX_DRIVE constant
- paths, maximum limit
- _MAX_PATH constant
- MAX_DRIVE constant
- _MAX_FNAME constant
- _MAX_EXT constant
- MAX_DIR constant
- MAX_EXT constant
ms.assetid: 2b5d0e43-1347-45b4-8397-24a8a45c444e
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c585afee6bbea3d0cc48b696bc005b9a8d6c7992
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="path-field-limits"></a>Límites del campo de ruta de acceso
## <a name="syntax"></a>Sintaxis  
  
```  
#include <stdlib.h>  
```  
  
## <a name="remarks"></a>Comentarios  
 Estas constantes definen la longitud máxima de la ruta de acceso y de los campos individuales dentro de dicha ruta.  
  
|Constante|Significado|  
|--------------|-------------|  
|`_MAX_DIR`|Longitud máxima de componentes de directorio|  
|`_MAX_DRIVE`|Longitud máxima de componentes de unidad|  
|`_MAX_EXT`|Longitud máxima de componentes de extensión|  
|`_MAX_FNAME`|Longitud máxima de componentes de nombre de archivo|  
|`_MAX_PATH`|Longitud máxima de ruta de acceso completa|  
  
> [!NOTE]
>  C Runtime admite longitudes de ruta de acceso de hasta 32 768 caracteres, pero depende del sistema operativo, específicamente del sistema de archivos, que se admitan o no estas rutas de acceso más largas. La suma de los campos no puede exceder `_MAX_PATH` a efectos de compatibilidad total con versiones anteriores de los sistemas de archivos FAT32. El sistema de archivos NTFS de [!INCLUDE[win2kfamily](../c-runtime-library/includes/win2kfamily_md.md)], [!INCLUDE[WinXpFamily](../atl/reference/includes/winxpfamily_md.md)], [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)] y Windows Vista es compatible con las rutas de acceso de hasta 32 768 caracteres de longitud, pero únicamente cuando se usan las API Unicode. Al usar nombres de ruta de acceso largos, agregue el prefijo \\\\?\ a la ruta de acceso y use las versiones Unicode de las funciones de C Runtime.  
  
## <a name="see-also"></a>Vea también  
 [Constantes globales](../c-runtime-library/global-constants.md)