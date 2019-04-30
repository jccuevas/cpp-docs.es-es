---
title: Extraer un miembro de biblioteca
ms.date: 11/04/2016
f1_keywords:
- Lib
helpviewer_keywords:
- LIB [C++], extracting library members
- EXTRACT library manager option
- libraries, extracting members
- -EXTRACT library manager option
- extracting library members
- /EXTRACT library manager option
ms.assetid: a2c5c2a1-9b7e-489a-a9a4-1dec694e1fc5
ms.openlocfilehash: 6c577300f747d6f546b7caa3c66bddd6a516e16b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62271325"
---
# <a name="extracting-a-library-member"></a>Extraer un miembro de biblioteca

Puede utilizar LIB para crear un archivo objeto (.obj) que contiene una copia de un miembro de una biblioteca existente. Para extraer una copia de un miembro, use la sintaxis siguiente:

```
LIB library /EXTRACT:member /OUT:objectfile
```

Este comando crea un archivo .obj denominado *objectfile* que contiene una copia de un `member` de un *biblioteca*. El `member` nombre distingue mayúsculas de minúsculas. Puede extraer a sólo un miembro en un solo comando. La opción /OUT es necesaria; No hay ningún nombre de salida predeterminado. Si un archivo denominado *objectfile* ya existe en el directorio especificado (o el directorio actual, si no se especifica ningún directorio con *objectfile*), el texto extraído *objectfile*reemplaza el archivo existente.

## <a name="see-also"></a>Vea también

[Referencia de LIB](lib-reference.md)
