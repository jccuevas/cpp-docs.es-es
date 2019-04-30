---
title: Advertencia del compilador (nivel 1) C4581
ms.date: 11/04/2016
f1_keywords:
- C4581
helpviewer_keywords:
- C4581
ms.assetid: 598bcd87-257d-4eb3-94e4-15bb31aadc99
ms.openlocfilehash: 9e370bcff0c30fb508ebc22aaff1f6a56dd420a1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397281"
---
# <a name="compiler-warning-level-1-c4581"></a>Advertencia del compilador (nivel 1) C4581

comportamiento desusado: "string1" reemplazado por 'cadena2' para procesar el atributo

Este error puede generarse como resultado del trabajo de conformidad del compilador efectuado para Visual C++ 2005: comprobación de parámetros de atributos de Visual C++.

En versiones anteriores, se han aceptado los valores de atributo se incluyen entre comillas o no. Si el valor es una enumeración, no debe incluirse entre comillas.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4581.

```
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