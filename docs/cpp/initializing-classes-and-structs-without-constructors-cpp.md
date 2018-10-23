---
title: Inicialización de clases y structs sin constructores (C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/17/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 3e55c3d6-1c6b-4084-b9e5-221b151402f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fb72bf8c8550d87a4e6bf86e440c7a468f4f878d
ms.sourcegitcommit: f9d9db80a8f13eae2c41337b974e1298109e33c5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2018
ms.locfileid: "49640764"
---
# <a name="initializing-classes-and-structs-without-constructors-c"></a>Inicialización de clases y structs sin constructores (C++)

No siempre es necesario definir un constructor para una clase, especialmente si son relativamente sencillas. Los usuarios pueden inicializar objetos de una clase o struct usando la inicialización uniforme, tal y como se muestra en el siguiente ejemplo:

```cpp
// no_constructor.cpp
// Compile with: cl /EHsc no_constructor.cpp
#include <time.h>

// No constructor
struct TempData
{
    int StationId;
    time_t timeSet;
    double current;
    double maxTemp;
    double minTemp;
};

// Has a constructor
struct TempData2
{
    TempData2(double minimum, double maximum, double cur, int id, time_t t) :
       stationId{id}, timeSet{t}, current{cur}, maxTemp{maximum}, minTemp{minimum} {}
    int stationId;
    time_t timeSet;
    double current;
    double maxTemp;
    double minTemp;
};

int main()
{
    time_t time_to_set;

    // Member initialization (in order of declaration):
    TempData td{ 45978, time(&time_to_set), 28.9, 37.0, 16.7 };

    // Default initialization = {0,0,0,0,0}
    TempData td_default{};

    // Uninitialized = if used, emits warning C4700 uninitialized local variable
    TempData td_noInit;

    // Member declaration (in order of ctor parameters)
    TempData2 td2{ 16.7, 37.0, 28.9, 45978, time(&time_to_set) };

    return 0;
}
```

Tenga en cuenta que cuando una clase o estructura no tiene ningún constructor, proporciona los elementos de lista en el orden en que los miembros se declaran en la clase. Si la clase tiene un constructor, que proporcionan los elementos en el orden de los parámetros.

## <a name="see-also"></a>Vea también

[Clases y structs](../cpp/classes-and-structs-cpp.md)<br/>
[Constructores](../cpp/constructors-cpp.md)
