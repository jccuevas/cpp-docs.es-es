---
title: Tools.ini y NMAKE
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, reading files
- Tools.ini and NMake
ms.assetid: ebd5eab6-ddf4-430e-bf4a-1db5bb84e344
ms.openlocfilehash: 38eebb3aaf07438da85b0cfe6bd3f26fb5d6db29
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57826864"
---
# <a name="toolsini-and-nmake"></a>Tools.ini y NMAKE

NMAKE lee Tools.ini antes de leer archivos MAKE, a menos que se usa/r. Busca Tools.ini en primer lugar en el directorio actual y, a continuación, en el directorio especificado por la variable de entorno INIT. La sección Configuración de NMAKE en el archivo de inicialización comienza con `[NMAKE]` y pueden contener cualquier información de archivo MAKE. Especifique un comentario en una línea independiente que comienza con un signo de número (#).

## <a name="see-also"></a>Vea también

[Ejecución de NMAKE](running-nmake.md)
