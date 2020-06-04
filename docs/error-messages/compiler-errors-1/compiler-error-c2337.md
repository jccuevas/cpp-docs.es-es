---
title: Error del compilador C2337
ms.date: 09/19/2019
f1_keywords:
- C2337
helpviewer_keywords:
- C2337
ms.assetid: eccc9178-a15e-42cd-bbd0-3cea7cf2d55b
ms.openlocfilehash: bf9b3e782804add13aeaef0e6672d2dd66d193be
ms.sourcegitcommit: f907b15f50a6b945d0b87c03af0050946157d701
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/20/2019
ms.locfileid: "71158772"
---
# <a name="compiler-error-c2337"></a>Error del compilador C2337

> '*Attribute-Name*': no se encontró el atributo

El código usa un atributo que no se admite en este contexto. O bien, el atributo no está disponible en esta versión del compilador. Para resolver este problema, quite el atributo no compatible.

El ejemplo siguiente genera la advertencia C2337:

```cpp
// C2337.cpp
// compile with: /c
[emitidl];
[module(name="x")];
[grasshopper]   // C2337, not a supported attribute
class a{};
```
