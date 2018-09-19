---
title: Error del compilador C3292 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3292
dev_langs:
- C++
helpviewer_keywords:
- C3292
ms.assetid: ead485cc-5471-4e10-b361-300589ff5b70
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8fc5f89978a7ecaff526fa05ca7a47494aada987
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46112465"
---
# <a name="compiler-error-c3292"></a>Error del compilador C3292

el espacio de nombres cli no se puede abrir de nuevo

El espacio de nombres cli no se puede declarar en su código.  Para obtener más información, consulte [de plataforma, predeterminado y cli de espacios de nombres](../../windows/platform-default-and-cli-namespaces-cpp-component-extensions.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C3292.

```
// C3292.cpp
// compile with: /clr /c
namespace cli {};   // C3292
```