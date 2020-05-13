---
title: Clase FrontEndFile
description: La referencia de clase FrontEndFile del SDK de Compilación de C++.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FrontEndFile
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c40137724279ea2fd615729db39f0ac5c907b79e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324758"
---
# <a name="frontendfile-class"></a>Clase FrontEndFile

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `FrontEndFile` clase se utiliza con las funciones [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)y [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilícelo para que coincida con un evento [FRONT_END_FILE.](../event-table.md#front-end-file)

## <a name="syntax"></a>Sintaxis

```cpp
class FrontEndFile : public Activity
{
public:
    FrontEndFile(const RawEvent& event);

    const char* Path() const;
};
```

## <a name="members"></a>Miembros

Junto con los miembros heredados `FrontEndFile` de su clase base [Activity,](activity.md) la clase contiene los siguientes miembros:

### <a name="constructors"></a>Constructores

[FrontEndFile](#front-end-file)

### <a name="functions"></a>Functions

[Path](#path)

## <a name="frontendfile"></a><a name="front-end-file"></a>FrontEndFile

```cpp
FrontEndFile(const RawEvent& event);
```

### <a name="parameters"></a>Parámetros

*Evento*\
Un evento [FRONT_END_FILE.](../event-table.md#front-end-file)

## <a name="path"></a><a name="path"></a>Camino

```cpp
const char* Path() const;
```

### <a name="return-value"></a>Valor devuelto

La ruta absoluta al archivo, codificada en UTF-8.

::: moniker-end
