---
title: Error del compilador C2393
ms.date: 11/04/2016
f1_keywords:
- C2393
helpviewer_keywords:
- C2393
ms.assetid: 4bd95728-e813-4ce8-844a-c6ebe235ca82
ms.openlocfilehash: 39ca693aed3f08e7b2df3d687f94d93384393f23
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62302402"
---
# <a name="compiler-error-c2393"></a>Error del compilador C2393

> '*símbolo*': símbolo por appdomain no se puede asignar en el segmento '*segmento*'

## <a name="remarks"></a>Comentarios

El **/CLR: pure** y **/CLR: safe** opciones del compilador están en desuso en Visual Studio 2015 y no se admite en Visual Studio 2017.

El uso de [appdomain](../../cpp/appdomain.md) variables implica que está compilando con **/CLR: pure** o **/CLR: safe**, y una imagen pura o segura no puede contener segmentos de datos.

Consulte [/CLR (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md) para obtener más información.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C2393. Para corregir este problema, no cree un segmento de datos.

```cpp
// C2393.cpp
// compile with: /clr:pure /c
#pragma data_seg("myseg")
int n = 0;   // C2393
```