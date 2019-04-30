---
title: Error del compilador C2632
ms.date: 11/04/2016
f1_keywords:
- C2632
helpviewer_keywords:
- C2632
ms.assetid: b15a6b1b-42d2-4e1b-8660-e6bfde61052d
ms.openlocfilehash: b92d44bcfd04d4de7b39c5bdab5ee146d9b6693b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62257639"
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