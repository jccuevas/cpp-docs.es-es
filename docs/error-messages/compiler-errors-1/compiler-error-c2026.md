---
title: Error del compilador C2026 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2026
dev_langs:
- C++
helpviewer_keywords:
- C2026
ms.assetid: 8e64b6e1-b967-479b-be97-d12dc4a8e389
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 055ac47d036a1027817aa6b3433bfe0e2e88570e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46019554"
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