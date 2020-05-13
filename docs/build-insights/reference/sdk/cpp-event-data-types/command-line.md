---
title: Clase CommandLine
description: La referencia de la clase CommandLine del SDK de Compilación de C+++ .
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CommandLine
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b35d688acf06579cc27f2fee053ef58032e204e0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325059"
---
# <a name="commandline-class"></a>Clase CommandLine

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `CommandLine` clase se utiliza con las funciones [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)y [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilícelo para que coincida con un evento [COMMAND_LINE.](../event-table.md#command-line)

## <a name="syntax"></a>Sintaxis

```cpp
class CommandLine : public SimpleEvent
{
public:
    CommandLine(const RawEvent& event);

    const wchar_t* Value() const;
};
```

## <a name="members"></a>Miembros

Junto con los miembros heredados de `CommandLine` su clase base [SimpleEvent,](simple-event.md) la clase contiene los siguientes miembros:

### <a name="constructors"></a>Constructores

[Commandline](#command-line)

### <a name="functions"></a>Functions

[Valor](#value)

## <a name="commandline"></a><a name="command-line"></a>Commandline

```cpp
CommandLine(const RawEvent& event);
```

### <a name="parameters"></a>Parámetros

*Evento*\
Un evento [COMMAND_LINE.](../event-table.md#command-line)

## <a name="value"></a><a name="value"></a> Valor

```cpp
const wchar_t Value() const;
```

### <a name="return-value"></a>Valor devuelto

Cadena que contiene una línea de comandos. El valor incluye argumentos que se obtuvieron de un archivo \_de\_respuesta y \_\_de variables de entorno como CL, CL, Link y LINK .

::: moniker-end
