---
title: Error del compilador C2195
ms.date: 11/04/2016
f1_keywords:
- C2195
helpviewer_keywords:
- C2195
ms.assetid: 9f9f035c-9c51-4173-a8ea-c6f907fc5c63
ms.openlocfilehash: 748516dbcdf5e135964e720d6215f31091bfed9e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758533"
---
# <a name="compiler-error-c2195"></a>Error del compilador C2195

' Identifier ': es un segmento de datos

La pragma `code_seg` usa un nombre de segmento que se usa con la pragma `data_seg`.

En el ejemplo siguiente se genera C2195:

```cpp
// C2195.cpp
#pragma data_seg("MYDATA")
#pragma code_seg("MYDATA")   // C2195
#pragma code_seg("MYDATA2")   // OK
```
