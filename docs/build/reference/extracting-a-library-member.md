---
title: Extraer un miembro de biblioteca
ms.date: 11/04/2016
helpviewer_keywords:
- LIB [C++], extracting library members
- EXTRACT library manager option
- libraries, extracting members
- -EXTRACT library manager option
- extracting library members
- /EXTRACT library manager option
ms.assetid: a2c5c2a1-9b7e-489a-a9a4-1dec694e1fc5
ms.openlocfilehash: 874866627099eb5aeb318273db26a976e99bac7f
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439881"
---
# <a name="extracting-a-library-member"></a>Extraer un miembro de biblioteca

Puede usar LIB para crear un archivo de objeto (. obj) que contenga una copia de un miembro de una biblioteca existente. Para extraer una copia de un miembro, use la siguiente sintaxis:

```
LIB library /EXTRACT:member /OUT:objectfile
```

Este comando crea un archivo. obj denominado *objectfile* que contiene una copia de una `member` de una *biblioteca*. El nombre del `member` distingue mayúsculas de minúsculas. Solo puede extraer un miembro de un solo comando. Se requiere la opción/OUT; no hay ningún nombre de salida predeterminado. Si ya existe un archivo denominado *objectfile* en el directorio especificado (o en el directorio actual, si no se especifica ningún directorio con *objectfile*), el *objectfile* extraído reemplaza el archivo existente.

## <a name="see-also"></a>Consulte también

[Referencia de LIB](lib-reference.md)
