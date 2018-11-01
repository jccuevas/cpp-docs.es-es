---
title: Error del compilador C2632
ms.date: 11/04/2016
f1_keywords:
- C2632
helpviewer_keywords:
- C2632
ms.assetid: b15a6b1b-42d2-4e1b-8660-e6bfde61052d
ms.openlocfilehash: b92d44bcfd04d4de7b39c5bdab5ee146d9b6693b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50437938"
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