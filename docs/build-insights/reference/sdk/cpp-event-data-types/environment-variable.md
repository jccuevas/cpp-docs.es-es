---
title: Clase EnvironmentVariable
description: Referencia C++ de la clase ENVIRONMENTVARIABLE del SDK de Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EnvironmentVariable
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 19e9278e76fb2116dac30a0e790fba86c6c56484
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334929"
---
# <a name="environmentvariable-class"></a>Clase EnvironmentVariable

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La clase `EnvironmentVariable` se usa con las funciones [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)y [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Úselo para que coincida con un evento de [ENVIRONMENT_VARIABLE](../event-table.md#environment-variable) .

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

Junto con los miembros heredados de su clase base [SimpleEvent](simple-event.md) , la clase `EnvironmentVariable` contiene los siguientes miembros:

### <a name="constructors"></a>Constructores

[EnvironmentVariable](#environment-variable)

### <a name="functions"></a>Funciones

[Name](#name)
[Value](#value)

## <a name="environment-variable"></a>EnvironmentVariable

```cpp
EnvironmentVariable(const RawEvent& event);
```

### <a name="parameters"></a>Parámetros

*event*\
Un evento de [ENVIRONMENT_VARIABLE](../event-table.md#environment-variable) .

## <a name="name"></a> Name

```cpp
const wchar_t Name() const;
```

### <a name="return-value"></a>Valor devuelto

Nombre de la variable de entorno.

## <a name="value"></a>Valor

```cpp
const wchar_t Value() const;
```

### <a name="return-value"></a>Valor devuelto

Valor de la variable de entorno.

::: moniker-end
