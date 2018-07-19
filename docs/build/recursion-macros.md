---
title: Macros de recursividad | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, recursion macros
- recursion macros
- macros, recursion
ms.assetid: c53e5ae7-619e-46b1-bdc2-86d8c7798b1d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2759deaff6014cbba40c97f9d627baf6a800732f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368966"
---
# <a name="recursion-macros"></a>Macros de recursividad
Usar macros de recursividad para llamar a NMAKE de forma recursiva. Las sesiones recursivas heredan macros de línea de comandos y variables de entorno e información de Tools.ini. No heredan reglas de inferencia definidas por el archivo MAKE o **. SUFIJOS** y **. Muy VALIOSO** especificaciones. Para pasar macros a una sesión NMAKE recursiva, establecer una variable de entorno con SET antes de la llamada recursiva, defina una macro en el comando para la llamada recursiva o definir una macro en Tools.ini.  
  
|Macro|de esquema JSON|  
|-----------|----------------|  
|**ASEGÚRESE DE**|Comando usado originalmente para llamar a NMAKE.<br /><br /> La macro $ (Make) proporciona la ruta de acceso completa a nmake.exe.|  
|**MAKEDIR**|Directorio actual cuando se llamó a NMAKE.|  
|**MAKEFLAGS**|Opciones actualmente en vigor. Usar como `/$(MAKEFLAGS)`.  Tenga en cuenta que /F no se incluye.|  
  
## <a name="see-also"></a>Vea también  
 [Macros NMAKE especiales](../build/special-nmake-macros.md)