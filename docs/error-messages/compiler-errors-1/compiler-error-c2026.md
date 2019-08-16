---
title: Error del compilador C2026
ms.date: 11/04/2016
f1_keywords:
- C2026
helpviewer_keywords:
- C2026
ms.assetid: 8e64b6e1-b967-479b-be97-d12dc4a8e389
ms.openlocfilehash: da4c03c681f95efaa5edb159869315b41d027e99
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62303533"
---
# <a name="compiler-error-c2026"></a>Error del compilador C2026

cadena demasiado grande, caracteres finales truncados

La cadena era mayor que el límite de 16380 caracteres de byte único.

Antes de la concatenación de cadenas adyacentes, una cadena no puede tener más de 16380 caracteres de byte único.

Una cadena Unicode de aproximadamente la mitad de esta longitud también generará este error.

Si tiene una cadena que se define como sigue, generará un error C2026:

```
char sz[] =
"\
imagine a really, really \
long string here\
";
```

Se podría dividirla como sigue:

```
char sz[] =
"\
imagine a really, really "
"long string here\
";
```

Es posible que desee almacenar los literales de cadena excepcionalmente grande (32 KB o más) en un recurso personalizado o un archivo externo. Consulte [crear un nuevo personalizado o recurso de datos](../../windows/creating-a-new-custom-or-data-resource.md) para obtener más información.