---
title: Compilador advertencia (nivel 4) C4233 | Documentos de Microsoft
ms.custom: ''
ms.date: 10/25/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4233
dev_langs:
- C++
helpviewer_keywords:
- C4233
ms.assetid: 9aa51fc6-8ef3-43b5-bafb-c9333cf60de3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a933d41fd8e7cf3b94e458efff72193b8ce5e187
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4233"></a>Advertencia del compilador (nivel 4) C4233

> ha utilizado una extensión no estándar: '*palabra clave*' palabra clave solo se admite en C++, no en C

El compilador compila el código fuente como C en lugar de C++, y se utilizó una palabra clave que solo es válida en C++. El compilador compila el archivo de código fuente como C si la extensión del archivo de origen es .c o usar [/TC](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md).

Esta advertencia suele convertirse automáticamente en un error. Si desea modificar este comportamiento, utilice [#pragma warning](../../preprocessor/warning.md). Por ejemplo, para convertir C4233 en un problema de la advertencia de nivel 4, agregue esta línea al archivo de código fuente:

```cpp
#pragma warning(4:4233)
```
