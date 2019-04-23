---
title: Error del compilador C3106
ms.date: 11/04/2016
f1_keywords:
- C3106
helpviewer_keywords:
- C3106
ms.assetid: 39d97a32-0905-4702-87d3-7f8ce473fb93
ms.openlocfilehash: c5ed544549aecd9811279e065d7c252fe085e545
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59775994"
---
# <a name="compiler-error-c3106"></a>Error del compilador C3106

'attribute': los argumentos sin nombre deben preceder a los argumentos con nombre

Argumentos sin nombre deben pasarse a un atributo antes de argumentos con nombre.

Para obtener más información, consulte [User-Defined Attributes](../../extensions/user-defined-attributes-cpp-component-extensions.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C3106.

```
// C3106.cpp
// compile with: /c
[module(name="MyLib", dll)];   // C3106
[module(dll, name="MyLib")];   // OK
```