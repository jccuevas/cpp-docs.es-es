---
title: Múltiples archivos en línea | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inline files, multiple NMAKE
- multiple inline files
- NMAKE program, inline files
ms.assetid: 6d381dcf-0ed8-45d1-8df3-b4598d860b99
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 87d68034c4f0018d65020915d24d0b5c2ec5d61a
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45725600"
---
# <a name="multiple-inline-files"></a>Múltiples archivos en línea

Un comando puede crear más de un archivo en línea.

## <a name="syntax"></a>Sintaxis

```
command << <<
inlinetext
<<[KEEP | NOKEEP]
inlinetext
<<[KEEP | NOKEEP]
```

## <a name="remarks"></a>Comentarios

Para cada archivo, especifique una o varias líneas de texto en línea seguida de una línea de cierre que contiene el delimitador. Comience el texto del segundo archivo en la línea siguiente a la línea de delimitador para el primer archivo.

## <a name="see-also"></a>Vea también

[Archivos insertados en un archivo MAKE](../build/inline-files-in-a-makefile.md)