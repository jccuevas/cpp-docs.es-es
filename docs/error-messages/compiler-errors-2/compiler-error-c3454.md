---
title: Error del compilador C3454 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3454
dev_langs:
- C++
helpviewer_keywords:
- C3454
ms.assetid: dc4e6d57-5b4d-4114-8d6f-22f9ae62925b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e469f6715775288720c61ad8a61e16956e4c63d1
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2018
ms.locfileid: "48789168"
---
# <a name="compiler-error-c3454"></a>Error del compilador C3454

No se permite [attribute] en la declaración de clase

Debe definir una clase para que sea un atributo.

Para obtener más información, consulte [atributo](../../windows/attributes/attribute.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C3454:

```
// C3454.cpp
// compile with: /clr /c
using namespace System;

[attribute]   // C3454
ref class Attr1;

[attribute]   // OK
ref class Attr2 {};
```