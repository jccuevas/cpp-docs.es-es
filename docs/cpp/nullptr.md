---
title: nullptr
ms.date: 11/04/2016
f1_keywords:
- nullptr_cpp
helpviewer_keywords:
- nullptr keyword [C++]
ms.assetid: e9d80ea6-2506-4eb5-b47b-2349df085832
ms.openlocfilehash: 51df20ea00e5dd77ab1fc1a2a01253b8f788ad0a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358853"
---
# <a name="nullptr"></a>nullptr

Designa una constante de puntero null de tipo `std::nullptr_t`, que se puede convertir a cualquier tipo de puntero sin formato.  Aunque puede usar la palabra clave **nullptr** sin incluir `std::nullptr_t`ningún encabezado, si el código `<cstddef>`usa el tipo , debe definirlo incluyendo el encabezado .

> [!NOTE]
> La palabra clave **nullptr** también se define en C++/CLI para aplicaciones de código administrado y no es intercambiable con la palabra clave ISO Standard C++. Si el código se puede compilar mediante la opción del compilador `__nullptr` [/clr,](../build/reference/clr-common-language-runtime-compilation.md) que tiene como destino el código administrado, use en cualquier línea de código donde debe garantizar que el compilador usa la interpretación nativa de C++. Para obtener más información, vea [nullptr](../extensions/nullptr-cpp-component-extensions.md).

## <a name="remarks"></a>Observaciones

Evite usar NULL`0`o cero ( ) como una constante de puntero nulo; **nullptr** es menos vulnerable al mal uso y funciona mejor en la mayoría de las situaciones.  Por ejemplo, dado `func(std::pair<const char *, double>)`, la llamada a `func(std::make_pair(NULL, 3.14))` produce un error del compilador.  La macro NULL se expande a `0`, de modo que la llamada `std::make_pair(0, 3.14)` devuelve `std::pair<int, double>`, que no se puede convertir al tipo de parámetro `std::pair<const char *, double>` de func().  La llamada a `func(std::make_pair(nullptr, 3.14))` se compila correctamente porque `std::make_pair(nullptr, 3.14)` devuelve `std::pair<std::nullptr_t, double>`, que se puede convertir en `std::pair<const char *, double>`.

## <a name="see-also"></a>Consulte también

[Palabras clave](../cpp/keywords-cpp.md)<br/>
[nullptr](../extensions/nullptr-cpp-component-extensions.md)(C++/CLI)
