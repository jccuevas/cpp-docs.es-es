---
title: Error del compilador C2393
ms.date: 11/04/2016
f1_keywords:
- C2393
helpviewer_keywords:
- C2393
ms.assetid: 4bd95728-e813-4ce8-844a-c6ebe235ca82
ms.openlocfilehash: cc3c124f1a4daea0f2517a93c6b354b8233aa5e5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205990"
---
# <a name="compiler-error-c2393"></a>Error del compilador C2393

> '*Symbol*': el símbolo por AppDomain no se puede asignar en el segmento '*Segment*'

## <a name="remarks"></a>Observaciones

Las opciones del compilador **/clr: Pure** y **/clr: Safe** están en desuso en Visual Studio 2015 y no se admiten en Visual Studio 2017.

El uso de variables de [AppDomain](../../cpp/appdomain.md) implica que se compila con **/clr: Pure** o **/clr: Safe**, y una imagen segura o pura no puede contener segmentos de datos.

Consulte [/CLR (compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) para obtener más información.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C2393. Para corregir este problema, no cree un segmento de datos.

```cpp
// C2393.cpp
// compile with: /clr:pure /c
#pragma data_seg("myseg")
int n = 0;   // C2393
```
