---
title: Clase EnvironmentVariable
description: La referencia de clase EnvironmentVariable del SDK de C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EnvironmentVariable
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 963c52e0ea9e048448c6f2b3ac62d9938817467e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325016"
---
# <a name="environmentvariable-class"></a>Clase EnvironmentVariable

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `EnvironmentVariable` clase se utiliza con las funciones [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)y [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilícelo para que coincida con un evento [ENVIRONMENT_VARIABLE.](../event-table.md#environment-variable)

## <a name="syntax"></a>Sintaxis

```cpp
class EnvironmentVariable : public SimpleEvent
{
public:
    EnvironmentVariable(const RawEvent& event);

    const wchar_t* Name() const;
    const wchar_t* Value() const;
};
```

## <a name="members"></a>Miembros

Junto con los miembros heredados de `EnvironmentVariable` su clase base [SimpleEvent,](simple-event.md) la clase contiene los siguientes miembros:

### <a name="constructors"></a>Constructores

[EnvironmentVariable](#environment-variable)

### <a name="functions"></a>Functions

[Name](#name)
[Valor del](#value) nombre

## <a name="environmentvariable"></a><a name="environment-variable"></a>EnvironmentVariable

```cpp
EnvironmentVariable(const RawEvent& event);
```

### <a name="parameters"></a>Parámetros

*Evento*\
Un evento [ENVIRONMENT_VARIABLE.](../event-table.md#environment-variable)

## <a name="name"></a><a name="name"></a>Nombre

```cpp
const wchar_t Name() const;
```

### <a name="return-value"></a>Valor devuelto

Nombre de la variable de entorno.

## <a name="value"></a><a name="value"></a> Valor

```cpp
const wchar_t Value() const;
```

### <a name="return-value"></a>Valor devuelto

Valor de la variable de entorno.

::: moniker-end
