---
title: Reutilizar archivos en línea | Microsoft Docs
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
ms.openlocfilehash: 37544db8076d40e638b6ddf6f340070298229149
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45722467"
---
# <a name="reusing-inline-files"></a>Reutilizar archivos en línea

Para reutilizar un archivo en línea, especifique <<*filename* donde se define el archivo y se usa por primera vez, a continuación, volver a usar *filename* sin << más adelante en el mismo o en otro comando. Debe ejecutar el comando para crear el archivo en línea antes de todos los comandos que utilizan el archivo.

## <a name="see-also"></a>Vea también

[Archivos insertados en un archivo MAKE](../build/inline-files-in-a-makefile.md)