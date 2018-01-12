---
title: Macros de recursividad | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- NMAKE program, recursion macros
- recursion macros
- macros, recursion
ms.assetid: c53e5ae7-619e-46b1-bdc2-86d8c7798b1d
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e8d9ef7f194151fb3259712759d0c29ed157d564
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="recursion-macros"></a>Macros de recursividad
Usar macros de recursividad para llamar a NMAKE de forma recursiva. Las sesiones recursivas heredan macros de línea de comandos y variables de entorno e información de Tools.ini. No heredan reglas de inferencia definidas por el archivo MAKE o **. SUFIJOS** y **. Muy VALIOSO** especificaciones. Para pasar macros a una sesión NMAKE recursiva, establecer una variable de entorno con SET antes de la llamada recursiva, defina una macro en el comando para la llamada recursiva o definir una macro en Tools.ini.  
  
|Macro|Definición|  
|-----------|----------------|  
|**ASEGÚRESE DE**|Comando usado originalmente para llamar a NMAKE.<br /><br /> La macro $ (Make) proporciona la ruta de acceso completa a nmake.exe.|  
|**MAKEDIR**|Directorio actual cuando se llamó a NMAKE.|  
|**MAKEFLAGS**|Opciones actualmente en vigor. Usar como `/$(MAKEFLAGS)`.  Tenga en cuenta que /F no se incluye.|  
  
## <a name="see-also"></a>Vea también  
 [Macros NMAKE especiales](../build/special-nmake-macros.md)