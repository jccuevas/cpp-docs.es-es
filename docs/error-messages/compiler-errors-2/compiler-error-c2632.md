---
title: Error del compilador C2632 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2632
dev_langs:
- C++
helpviewer_keywords:
- C2632
ms.assetid: b15a6b1b-42d2-4e1b-8660-e6bfde61052d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7bf03c35c60bebb52c94ed04cca2349f35c06fbc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46093655"
---
# <a name="compiler-error-c2632"></a>Error del compilador C2632

'type1' seguido por 'type2' no es válido

Este error puede deberse a falta código entre dos especificadores de tipo.

El ejemplo siguiente genera C2632:

```
// C2632.cpp
int float i;   // C2632
```

Este error también puede generarse como resultado del trabajo de conformidad del compilador efectuado para Visual Studio .NET 2003. `bool` Ahora es un tipo adecuado. En versiones anteriores, `bool` era una definición de tipo, y puede crear identificadores con ese nombre.

El ejemplo siguiente genera C2632:

```
// C2632_2.cpp
// compile with: /LD
void f(int bool);   // C2632
```

Para resolver este error para que el código es válido en las versiones tanto el Visual Studio .NET 2003 y Visual Studio .NET de Visual C++, cambie el nombre del identificador.