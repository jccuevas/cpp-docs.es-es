---
title: Tools.ini y NMAKE | Documentos de Microsoft
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
- NMAKE program, reading files
- Tools.ini and NMake
ms.assetid: ebd5eab6-ddf4-430e-bf4a-1db5bb84e344
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0e4516c3206a08c2b9ee32aea4bbb669ce4cdf0d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="toolsini-and-nmake"></a>Tools.ini y NMAKE
NMAKE lee Tools.ini antes de leer archivos MAKE, a menos que se usa/r. Busca Tools.ini en primer lugar en el directorio actual y, a continuación, en el directorio especificado por la variable de entorno INIT. La sección Configuración de NMAKE en el archivo de inicialización empieza con `[NMAKE]` y pueden contener cualquier información de archivos MAKE. Escriba un comentario en una línea independiente que comience con un signo de número (#).  
  
## <a name="see-also"></a>Vea también  
 [Ejecución de NMAKE](../build/running-nmake.md)