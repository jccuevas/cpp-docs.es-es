---
title: Compilador advertencia (nivel 4) C4233 | Documentos de Microsoft
ms.custom: 
ms.date: 10/25/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4233
dev_langs:
- C++
helpviewer_keywords:
- C4233
ms.assetid: 9aa51fc6-8ef3-43b5-bafb-c9333cf60de3
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ad27d2ec3d59df147d8bfc26372a2d25397e651f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4233"></a>Advertencia del compilador (nivel 4) C4233

> ha utilizado una extensión no estándar: '*palabra clave*' palabra clave solo se admite en C++, no en C

El compilador compila el código fuente como C en lugar de C++, y se utilizó una palabra clave que solo es válida en C++. El compilador compila el archivo de código fuente como C si la extensión del archivo de origen es .c o usar [/TC](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md).

Esta advertencia suele convertirse automáticamente en un error. Si desea modificar este comportamiento, utilice [#pragma warning](../../preprocessor/warning.md). Por ejemplo, para convertir C4233 en un problema de la advertencia de nivel 4, agregue esta línea al archivo de código fuente:

```cpp
#pragma warning(4:4233)
```
