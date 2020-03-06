---
title: CommandLine (clase)
description: Referencia C++ de la clase COMMANDLINE del SDK de Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CommandLine
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ff16646920fe77f7f3b4cb8a194a38984c3e6c32
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334989"
---
# <a name="commandline-class"></a>CommandLine (clase)

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La clase `CommandLine` se usa con las funciones [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)y [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Úselo para que coincida con un evento de [COMMAND_LINE](../event-table.md#command-line) .

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

Junto con los miembros heredados de su clase base [SimpleEvent](simple-event.md) , la clase `CommandLine` contiene los siguientes miembros:

### <a name="constructors"></a>Constructores

[CommandLine](#command-line)

### <a name="functions"></a>Funciones

[Valor](#value)

## <a name="command-line"></a>CommandLine

```cpp
CommandLine(const RawEvent& event);
```

### <a name="parameters"></a>Parámetros

*event*\
Un evento de [COMMAND_LINE](../event-table.md#command-line) .

## <a name="value"></a>Valor

```cpp
const wchar_t Value() const;
```

### <a name="return-value"></a>Valor devuelto

Cadena que contiene una línea de comandos. El valor incluye los argumentos que se obtuvieron de un archivo de respuesta y de las variables de entorno como CL, \_\_de CL, vínculo y \_vínculo\_.

::: moniker-end
