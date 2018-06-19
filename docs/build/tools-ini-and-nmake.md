---
title: Tools.ini y NMAKE | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, reading files
- Tools.ini and NMake
ms.assetid: ebd5eab6-ddf4-430e-bf4a-1db5bb84e344
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 860a334274a3a1a4ac9e11c3e7b5e9a0f136ecc0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32380555"
---
# <a name="toolsini-and-nmake"></a>Tools.ini y NMAKE
NMAKE lee Tools.ini antes de leer archivos MAKE, a menos que se usa/r. Busca Tools.ini en primer lugar en el directorio actual y, a continuación, en el directorio especificado por la variable de entorno INIT. La sección Configuración de NMAKE en el archivo de inicialización empieza con `[NMAKE]` y pueden contener cualquier información de archivos MAKE. Escriba un comentario en una línea independiente que comience con un signo de número (#).  
  
## <a name="see-also"></a>Vea también  
 [Ejecución de NMAKE](../build/running-nmake.md)