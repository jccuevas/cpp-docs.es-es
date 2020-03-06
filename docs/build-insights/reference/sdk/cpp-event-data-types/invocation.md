---
title: Invocación (clase)
description: La C++ referencia de clase de invocación del SDK de Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Invocation
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 0c4698300a3eeaf77210ad74f84b0c0cd219b457
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334749"
---
# <a name="invocation-class"></a>Invocación (clase)

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La clase `Invocation` se usa con las funciones [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)y [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Úselo para buscar coincidencias con un evento de [compilador](../event-table.md#compiler) o [vinculador](../event-table.md#linker) .

## <a name="syntax"></a>Sintaxis

```cpp
class Invocation : public Activity
{
    const INVOCATION_DATA* data_;

public:
    enum class Type
    {
        CL      = MSVC_TOOL_CODE_CL,
        LINK    = MSVC_TOOL_CODE_LINK
    };

    Invocation(const RawEvent& event);

    Type             Type() const;
    const char*      ToolVersionString() const;
    const wchar_t*   WorkingDirectory() const;
    const wchar_t*   ToolPath() const;

    const INVOCATION_VERSION_DATA& ToolVersion() const;
};
```

## <a name="members"></a>Miembros

Junto con los miembros heredados de su clase base de [actividad](activity.md) , la clase `Invocation` contiene los siguientes miembros:

### <a name="constructors"></a>Constructores

[Invocación](#invocation)

### <a name="functions"></a>Funciones

[ToolVersion](#tool-version)

de la
[trayectoria](#tool-path) de la [ToolVersionString](#tool-version-string) [tipo](#type)
[WorkingDirectory](#working-directory)

## <a name="invocation"></a>Invocación

```cpp
Invocation(const RawEvent& event);
```

### <a name="parameters"></a>Parámetros

*event*\
Un [compilador](../event-table.md#compiler) o un evento del [vinculador](../event-table.md#linker) .

## <a name="tool-path"></a>ToolPath

```cpp
const wchar_t* ToolPath() const;
```

### <a name="return-value"></a>Valor devuelto

La ruta de acceso absoluta a la herramienta que se invocó.

## <a name="tool-version"></a>ToolVersion

```cpp
const INVOCATION_VERSION_DATA& ToolVersion() const;
```

### <a name="return-value"></a>Valor devuelto

Versión de la herramienta que se invocó, como referencia de [INVOCATION_VERSION_DATA](../c-event-data-types/invocation-version-data-struct.md) .

## <a name="tool-version-string"></a>ToolVersionString

```cpp
const char* ToolVersionString() const;
```

### <a name="return-value"></a>Valor devuelto

Versión de la herramienta que se invocó, como una cadena ANSI.

## <a name="type"></a>Automáticamente

```cpp
Type Type() const;
```

### <a name="return-value"></a>Valor devuelto

Código que indica la herramienta que se invocó.

## <a name="working-directory"></a>WorkingDirectory

```cpp
const wchar_t* WorkingDirectory() const;
```

### <a name="return-value"></a>Valor devuelto

La ruta de acceso absoluta al directorio en el que se invocó la herramienta.

::: moniker-end
