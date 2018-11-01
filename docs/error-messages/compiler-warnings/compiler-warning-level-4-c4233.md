---
title: Advertencia del compilador (nivel 4) C4233
ms.date: 10/25/2017
f1_keywords:
- C4233
helpviewer_keywords:
- C4233
ms.assetid: 9aa51fc6-8ef3-43b5-bafb-c9333cf60de3
ms.openlocfilehash: 361e00b7361aab51ea077d7e248503f3654e5e58
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50516524"
---
# <a name="compiler-warning-level-4-c4233"></a>Advertencia del compilador (nivel 4) C4233

> ha utilizado una extensión no estándar: '*palabra clave*' palabra clave solo se admite en C++, no en C

El compilador compila el código fuente como C, en lugar de C++, y ha utilizado una palabra clave que solo es válida en C++. El compilador compila el archivo de código fuente como C si la extensión del archivo de origen es .c o usar [/TC](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md).

Esta advertencia suele convertirse automáticamente en un error. Si desea modificar este comportamiento, use [advertencia #pragma](../../preprocessor/warning.md). Por ejemplo, para convertir C4233 en una advertencia de nivel 4, agregue esta línea al archivo de código fuente:

```cpp
#pragma warning(4:4233)
```
