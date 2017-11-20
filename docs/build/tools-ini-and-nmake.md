---
title: Tools.ini y NMAKE | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- NMAKE program, reading files
- Tools.ini and NMake
ms.assetid: ebd5eab6-ddf4-430e-bf4a-1db5bb84e344
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 638132f640fd342a752ec45541275178f6f26692
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="toolsini-and-nmake"></a>Tools.ini y NMAKE
NMAKE lee Tools.ini antes de leer archivos MAKE, a menos que se usa/r. Busca Tools.ini en primer lugar en el directorio actual y, a continuación, en el directorio especificado por la variable de entorno INIT. La sección Configuración de NMAKE en el archivo de inicialización empieza con `[NMAKE]` y pueden contener cualquier información de archivos MAKE. Escriba un comentario en una línea independiente que comience con un signo de número (#).  
  
## <a name="see-also"></a>Vea también  
 [Ejecución de NMAKE](../build/running-nmake.md)