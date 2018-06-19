---
title: Reutilizar archivos en línea | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inline files, reusing NMAKE
- revising inline files
- NMAKE program, inline files
ms.assetid: d42dbffb-2cef-4ccb-9a1f-20b8ef81481c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 017364061093ef7a3c3e006f58c331c48a8009e8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379905"
---
# <a name="reusing-inline-files"></a>Reutilizar archivos en línea
Para reutilizar un archivo en línea, especifique <<*filename* donde el archivo se define y se utilizó por primera vez, a continuación, volver a usar *filename* sin << más adelante en el mismo u otro comando. Debe ejecutar el comando para crear el archivo en línea antes de todos los comandos que utilizan el archivo.  
  
## <a name="see-also"></a>Vea también  
 [Archivos insertados en un archivo MAKE](../build/inline-files-in-a-makefile.md)