---
title: Clase de invocación
description: La referencia de clase de invocación del SDK de C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Invocation
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: fcb087d46ea445251b0108f811545a44c26f421e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324639"
---
# <a name="invocation-class"></a>Clase de invocación

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `Invocation` clase se utiliza con las funciones [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)y [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilícelo para que coincida con un evento [COMPILER](../event-table.md#compiler) o [LINKER.](../event-table.md#linker)

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

Junto con los miembros heredados `Invocation` de su clase base [Activity,](activity.md) la clase contiene los siguientes miembros:

### <a name="constructors"></a>Constructores

[Invocación](#invocation)

### <a name="functions"></a>Functions

[ToolPath](#tool-path)
[ToolVersion](#tool-version)
[ToolVersionString](#tool-version-string)
[Type](#type)
[WorkingDirectory](#working-directory)

## <a name="invocation"></a><a name="invocation"></a>Invocación

```cpp
Invocation(const RawEvent& event);
```

### <a name="parameters"></a>Parámetros

*Evento*\
Un evento [COMPILER](../event-table.md#compiler) o [LINKER.](../event-table.md#linker)

## <a name="toolpath"></a><a name="tool-path"></a>Trayectoria

```cpp
const wchar_t* ToolPath() const;
```

### <a name="return-value"></a>Valor devuelto

La ruta de acceso absoluta a la herramienta que se invocó.

## <a name="toolversion"></a><a name="tool-version"></a>ToolVersion

```cpp
const INVOCATION_VERSION_DATA& ToolVersion() const;
```

### <a name="return-value"></a>Valor devuelto

La versión de la herramienta que se invocó, como una referencia [INVOCATION_VERSION_DATA.](../c-event-data-types/invocation-version-data-struct.md)

## <a name="toolversionstring"></a><a name="tool-version-string"></a>ToolVersionString

```cpp
const char* ToolVersionString() const;
```

### <a name="return-value"></a>Valor devuelto

La versión de la herramienta que se invocó, como una cadena ANSI.

## <a name="type"></a>Tipo de <a name="type"></a>

```cpp
Type Type() const;
```

### <a name="return-value"></a>Valor devuelto

Código que indica la herramienta que se invocó.

## <a name="workingdirectory"></a><a name="working-directory"></a>WorkingDirectory

```cpp
const wchar_t* WorkingDirectory() const;
```

### <a name="return-value"></a>Valor devuelto

La ruta de acceso absoluta al directorio en el que se invocó la herramienta.

::: moniker-end
