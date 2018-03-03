---
title: Volcar importaciones de carga retrasada | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- delay-loaded imports, dumping
- imports (delay-loaded)
- delay-loaded imports
ms.assetid: f766acf4-9df8-4b85-8cf6-0be3ffc4c124
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3800d4863bc1aa3e3c847ff0cea886be2fede985
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="dumping-delay-loaded-imports"></a>Volcar importaciones de carga retrasada
Importaciones de carga retrasada se pueden volcar mediante [dumpbin /imports](../../build/reference/imports-dumpbin.md) y mostrarse con información ligeramente distinta de las importaciones estándar. Se segregan en su propia sección del volcado /imports y se etiquetan explícitamente como importaciones de carga retrasada. Si no hay que descargar información presente en la imagen, que se indica. Si no hay información de enlace, se indica la marca de fecha y hora de la DLL de destino junto con las direcciones de enlace de las importaciones.  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad del vinculador con las DLL de carga retrasada](../../build/reference/linker-support-for-delay-loaded-dlls.md)