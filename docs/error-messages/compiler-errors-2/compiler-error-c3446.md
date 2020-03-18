---
title: Error del compilador C3446
ms.date: 07/21/2017
f1_keywords:
- C3446
helpviewer_keywords:
- C3446
ms.assetid: 33064548-24e4-46f1-beb1-476e3c3b3fbf
ms.openlocfilehash: 0f9ebd274a90dffe00b0e8375cc374acf46e7a08
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447121"
---
# <a name="compiler-error-c3446"></a>Error del compilador C3446

>'*Class*': no se permite un inicializador de miembro predeterminado para un miembro de una clase Value

En Visual Studio 2015 y versiones anteriores, el compilador permitía (aunque omitía) un inicializador de miembro predeterminado para un miembro de una clase de valor. La inicialización predeterminada de una clase de valor siempre inicializa a cero a los miembros; no se permite un constructor predeterminado. En Visual Studio 2017, los inicializadores de miembro predeterminados generan un error del compilador, tal como se muestra en este ejemplo:

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C3446 en Visual Studio 2017 y versiones posteriores:

```cpp
// C3446.cpp
value struct V
{
       int i = 0; // error C3446: 'V::i': a default member initializer
                  // is not allowed for a member of a value class
       int j {0}; // C3446
};
```

Para corregir el error, quite el inicializador:

```cpp
// C3446b.cpp
value struct V
{
       int i;
       int j;
};
```

