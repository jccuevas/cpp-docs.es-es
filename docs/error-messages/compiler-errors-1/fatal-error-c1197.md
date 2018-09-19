---
title: Error irrecuperable C1197 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1197
dev_langs:
- C++
helpviewer_keywords:
- C1197
ms.assetid: 22b801b7-e792-41f6-a461-973c03c69f25
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 58561e7bd906fc750779ef53a4f68ec27088a3b7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46024767"
---
# <a name="fatal-error-c1197"></a>Error irrecuperable C1197

no puede hacer referencia 'a mscorlib.dll_1' porque el programa ya hacía referencia a ''a mscorlib.dll_2'

El compilador se asocia a una versión de common language runtime.  Sin embargo, se ha intentado hacer referencia a una versión de un archivo de common language runtime desde una versión anterior.

Para resolver este error, solo los archivos de referencia de la versión de common language runtime que se incluye con la versión de Visual C++ se compilación con.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C1197:

```
// C1197.cpp
// compile with: /clr /c
// processor: x86
#using "C:\Windows\Microsoft.NET\Framework\v1.1.4322\mscorlib.dll"   // C1197
// try the following line instead
// #using "mscorlib.dll"
```