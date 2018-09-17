---
title: Extraer un miembro de biblioteca | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- Lib
dev_langs:
- C++
helpviewer_keywords:
- LIB [C++], extracting library members
- EXTRACT library manager option
- libraries, extracting members
- -EXTRACT library manager option
- extracting library members
- /EXTRACT library manager option
ms.assetid: a2c5c2a1-9b7e-489a-a9a4-1dec694e1fc5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9207a77868b3257d09f0d9efe38e4765cb8f4906
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45726523"
---
# <a name="extracting-a-library-member"></a>Extraer un miembro de biblioteca

Puede utilizar LIB para crear un archivo objeto (.obj) que contiene una copia de un miembro de una biblioteca existente. Para extraer una copia de un miembro, use la sintaxis siguiente:

```
LIB library /EXTRACT:member /OUT:objectfile
```

Este comando crea un archivo .obj denominado *objectfile* que contiene una copia de un `member` de un *biblioteca*. El `member` nombre distingue mayúsculas de minúsculas. Puede extraer a sólo un miembro en un solo comando. La opción /OUT es necesaria; No hay ningún nombre de salida predeterminado. Si un archivo denominado *objectfile* ya existe en el directorio especificado (o el directorio actual, si no se especifica ningún directorio con *objectfile*), el texto extraído *objectfile*reemplaza el archivo existente.

## <a name="see-also"></a>Vea también

[Referencia de LIB](../../build/reference/lib-reference.md)