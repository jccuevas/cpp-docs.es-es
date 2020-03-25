---
title: nullptr
ms.date: 11/04/2016
f1_keywords:
- nullptr_cpp
helpviewer_keywords:
- nullptr keyword [C++]
ms.assetid: e9d80ea6-2506-4eb5-b47b-2349df085832
ms.openlocfilehash: 223f4c3e8c838698f9716e241543db405c9394af
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177773"
---
# <a name="nullptr"></a>nullptr

Designa una constante de puntero null de tipo `std::nullptr_t`, que se puede convertir a cualquier tipo de puntero sin formato.  Aunque puede usar la palabra clave **nullptr** sin incluir ningún encabezado, si el código usa el tipo `std::nullptr_t`, debe definirlo incluyendo el encabezado `<cstddef>`.

> [!NOTE]
>  La palabra clave **nullptr** también se define C++en/CLI para las aplicaciones de código administrado y no es intercambiable con C++ la palabra clave estándar ISO. Si el código se puede compilar con la opción del compilador [/CLR](../build/reference/clr-common-language-runtime-compilation.md) , que tiene como destino el código administrado, utilice `__nullptr` en cualquier línea de código en la que deba C++ garantizar que el compilador usa la interpretación nativa. Para obtener más información, vea [nullptr](../extensions/nullptr-cpp-component-extensions.md).

## <a name="remarks"></a>Observaciones

Evite utilizar NULL o cero (`0`) como una constante de puntero nulo; **nullptr** es menos vulnerable a los usos indebidos y funciona mejor en la mayoría de los casos.  Por ejemplo, dado `func(std::pair<const char *, double>)`, la llamada a `func(std::make_pair(NULL, 3.14))` produce un error del compilador.  La macro NULL se expande a `0`, de modo que la llamada `std::make_pair(0, 3.14)` devuelve `std::pair<int, double>`, que no se puede convertir al tipo de parámetro `std::pair<const char *, double>` de func().  La llamada a `func(std::make_pair(nullptr, 3.14))` se compila correctamente porque `std::make_pair(nullptr, 3.14)` devuelve `std::pair<std::nullptr_t, double>`, que se puede convertir en `std::pair<const char *, double>`.

## <a name="see-also"></a>Consulte también

[Palabras clave](../cpp/keywords-cpp.md)<br/>
[nullptr](../extensions/nullptr-cpp-component-extensions.md)(C++/CLI)
