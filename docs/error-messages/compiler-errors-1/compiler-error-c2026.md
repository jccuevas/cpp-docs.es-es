---
title: Error del compilador C2026
ms.date: 11/04/2016
f1_keywords:
- C2026
helpviewer_keywords:
- C2026
ms.assetid: 8e64b6e1-b967-479b-be97-d12dc4a8e389
ms.openlocfilehash: 9747b1edadc76ceeb502b2c6fd03496b91769f5a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208070"
---
# <a name="compiler-error-c2026"></a>Error del compilador C2026

cadena demasiado grande, caracteres finales truncados

La cadena era más larga que el límite de 16380 caracteres de un solo byte.

Antes de la concatenación de cadenas adyacentes, una cadena no puede tener más de 16380 caracteres de un solo byte.

Una cadena Unicode de aproximadamente una mitad esta longitud también generará este error.

Si tiene una cadena definida como sigue, genera C2026:

```
char sz[] =
"\
imagine a really, really \
long string here\
";
```

Podría dividirlo de la siguiente manera:

```
char sz[] =
"\
imagine a really, really "
"long string here\
";
```

Es posible que desee almacenar literales de cadena de gran tamaño (32K o más) en un recurso personalizado o en un archivo externo. Vea [crear un nuevo recurso personalizado o de datos](../../windows/creating-a-new-custom-or-data-resource.md) para obtener más información.
