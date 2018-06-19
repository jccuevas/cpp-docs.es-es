---
title: Enlazar importaciones | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- /DELAY:NOBIND linker option
- DELAY:NOBIND linker option
ms.assetid: bb766038-deb1-41b1-bcbc-29a30e8c1e2a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7519fb18ac7f24e79a5f7f664cb35f8eb5b3fd77
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368933"
---
# <a name="binding-imports"></a>Enlazar importaciones
El comportamiento predeterminado del vinculador es crear una tabla de direcciones de importación enlazable para la DLL de carga retrasada. Si la DLL está enlazada, la función auxiliar intentará utilizar la información de enlace en lugar de llamar **GetProcAddress** en cada una de las importaciones que se hace referencia. Si la marca de tiempo o la dirección preferida no coinciden con los de la DLL cargada, la función auxiliar supondrá la tabla de direcciones de importación enlazadas no está actualizada y actuará como si no existe.  
  
 Si no se pretende Enlazar importaciones de carga retrasada de DLL, especificar [/delay](../../build/reference/delay-delay-load-import-settings.md): nobind en la línea de comandos del vinculador impedirá que la tabla de direcciones de importación enlazadas que generado y mucho espacio en el archivo de imagen.  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad del vinculador con las DLL de carga retrasada](../../build/reference/linker-support-for-delay-loaded-dlls.md)