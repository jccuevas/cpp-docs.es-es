---
title: Tools.ini y NMAKE | Microsoft Docs
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
ms.openlocfilehash: 84406886c9aa0c0053ed7c183912bf8a7f1f4771
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45723585"
---
# <a name="toolsini-and-nmake"></a>Tools.ini y NMAKE

NMAKE lee Tools.ini antes de leer archivos MAKE, a menos que se usa/r. Busca Tools.ini en primer lugar en el directorio actual y, a continuación, en el directorio especificado por la variable de entorno INIT. La sección Configuración de NMAKE en el archivo de inicialización comienza con `[NMAKE]` y pueden contener cualquier información de archivo MAKE. Especifique un comentario en una línea independiente que comienza con un signo de número (#).

## <a name="see-also"></a>Vea también

[Ejecución de NMAKE](../build/running-nmake.md)