---
title: ADVERTENCIA del compilador (nivel 1) C4581
ms.date: 11/04/2016
f1_keywords:
- C4581
helpviewer_keywords:
- C4581
ms.assetid: 598bcd87-257d-4eb3-94e4-15bb31aadc99
ms.openlocfilehash: 5931516e3f4eba91c3b7a3ab4d0ca4979ce1ed84
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2019
ms.locfileid: "73965925"
---
# <a name="compiler-warning-level-1-c4581"></a>ADVERTENCIA del compilador (nivel 1) C4581

comportamiento en desuso: ' "string1" ' se ha reemplazado por ' cadena2 ' para procesar el atributo

Este error se puede generar como resultado del trabajo de conformidad del compilador realizado para Visual Studio 2005: comprobación de parámetros para los C++ atributos visuales.

En versiones anteriores, se aceptaban valores de atributo tanto si se encontraban entre comillas. Si el valor es una enumeración, no debe ir entre comillas.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4581.

```cpp
// C4581.cpp
// compile with: /c /W1
#include "unknwn.h"
[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface IMyI : IUnknown {};

[coclass, uuid(12345678-1111-2222-3333-123456789012), threading("free")]   // C4581
// try the following line instead
// [coclass, uuid(12345678-1111-2222-3333-123456789012), threading(free)]
class CSample : public IMyI {};
```