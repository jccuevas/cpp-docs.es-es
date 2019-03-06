---
title: Tools.ini y NMAKE
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, reading files
- Tools.ini and NMake
ms.assetid: ebd5eab6-ddf4-430e-bf4a-1db5bb84e344
ms.openlocfilehash: c50fef5d2fd36b8fb9327cad25bc5b2ab4ba61e2
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57419892"
---
# <a name="toolsini-and-nmake"></a>Tools.ini y NMAKE

NMAKE lee Tools.ini antes de leer archivos MAKE, a menos que se usa/r. Busca Tools.ini en primer lugar en el directorio actual y, a continuación, en el directorio especificado por la variable de entorno INIT. La sección Configuración de NMAKE en el archivo de inicialización comienza con `[NMAKE]` y pueden contener cualquier información de archivo MAKE. Especifique un comentario en una línea independiente que comienza con un signo de número (#).

## <a name="see-also"></a>Vea también

[Ejecución de NMAKE](../build/running-nmake.md)
