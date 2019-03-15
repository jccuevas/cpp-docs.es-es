---
title: Múltiples archivos en línea
ms.date: 11/04/2016
helpviewer_keywords:
- inline files, multiple NMAKE
- multiple inline files
- NMAKE program, inline files
ms.assetid: 6d381dcf-0ed8-45d1-8df3-b4598d860b99
ms.openlocfilehash: 71f17ff6717e717693facb21b4a4341a040b14c1
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57827435"
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

[Archivos insertados en un archivo MAKE](inline-files-in-a-makefile.md)
