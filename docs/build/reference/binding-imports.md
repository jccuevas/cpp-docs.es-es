---
title: Enlazar importaciones | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- /DELAY:NOBIND linker option
- DELAY:NOBIND linker option
ms.assetid: bb766038-deb1-41b1-bcbc-29a30e8c1e2a
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: cd9bee6423c0eea98941331dcff86c002dd4ef9d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="binding-imports"></a>Enlazar importaciones
El comportamiento predeterminado del vinculador es crear una tabla de direcciones de importación enlazable para la DLL de carga retrasada. Si la DLL está enlazada, la función auxiliar intentará utilizar la información de enlace en lugar de llamar **GetProcAddress** en cada una de las importaciones que se hace referencia. Si la marca de tiempo o la dirección preferida no coinciden con los de la DLL cargada, la función auxiliar supondrá la tabla de direcciones de importación enlazadas no está actualizada y actuará como si no existe.  
  
 Si no se pretende Enlazar importaciones de carga retrasada de DLL, especificar [/delay](../../build/reference/delay-delay-load-import-settings.md): nobind en la línea de comandos del vinculador impedirá que la tabla de direcciones de importación enlazadas que generado y mucho espacio en el archivo de imagen.  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad del vinculador con las DLL de carga retrasada](../../build/reference/linker-support-for-delay-loaded-dlls.md)