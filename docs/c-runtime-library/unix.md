---
title: UNIX | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- unix
dev_langs:
- C++
helpviewer_keywords:
- UNIX
- POSIX compatibility
- POSIX file names
- UNIX, compatibility
ms.assetid: 40792414-7a5b-415d-bfa8-2bfb1ebb3731
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: 500280e2818908930fe2e3fe2608e217e1ba4b49
ms.contentlocale: es-es
ms.lasthandoff: 05/18/2017

---
# <a name="unix"></a>UNIX
Si tiene previsto portar sus programas a UNIX, siga estas instrucciones:  
  
-   No elimine los archivos de encabezado del subdirectorio SYS. Puede colocar los archivos de encabezado SYS en otra parte solo si no tiene previsto transportar los programas a UNIX.  
  
-   Utilice el delimitador de ruta de acceso compatible con UNIX en rutinas que toman cadenas que representan rutas de acceso y nombres de archivo como argumentos. UNIX admite solo la barra inclinada (/) para este propósito, mientras que los sistemas operativos Win32 admiten la barra diagonal inversa (\\) y la barra inclinada (/). Por lo tanto, en esta documentación se utilizan barras inclinadas compatibles con UNIX como delimitadores de ruta de acceso en las instrucciones `#include`, por ejemplo. (Sin embargo, el shell de comandos del sistema operativo Windows, CMD. EXE, no admite la barra inclinada en comandos escritos en el símbolo del sistema).  
  
-   Use rutas de acceso y nombres de archivo que funcionen correctamente en UNIX, que distingue mayúsculas de minúsculas. El sistema de archivos de tabla de asignación de archivos (FAT) en sistemas operativos Win32 no distingue mayúsculas de minúsculas; el sistema de archivos NTFS mantiene las mayúsculas y minúsculas en los listados de directorio, pero las ignora en las búsquedas de archivos y en otras operaciones del sistema.  
  
    > [!NOTE]
    >  En esta versión de Visual C++, la información sobre la compatibilidad con UNIX se ha eliminado de las descripciones de las funciones.  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad](../c-runtime-library/compatibility.md)
