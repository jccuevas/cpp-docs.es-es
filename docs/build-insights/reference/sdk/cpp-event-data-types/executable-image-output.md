---
title: Clase ExecutableImageOutput
description: La referencia de clase ExecutableImageOutput del SDK de Compilación de C++ .
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ExecutableImageOutput
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 834689a3605b729260f2d4c925396ee1af1bb705
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324956"
---
# <a name="executableimageoutput-class"></a>Clase ExecutableImageOutput

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `ExecutableImageOutput` clase se utiliza con las funciones [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)y [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilícelo para que coincida con un evento [EXECUTABLE_IMAGE_OUTPUT.](../event-table.md#executable-image-output)

## <a name="syntax"></a>Sintaxis

```cpp
class ExecutableImageOutput : public FileOutput
{
public:
    ExecutableImageOutput(const RawEvent& event);
};
```

## <a name="members"></a>Miembros

Junto con los miembros heredados de `ExecutableImageOutput` su clase base [FileOutput,](file-output.md) la clase contiene los siguientes miembros:

### <a name="constructors"></a>Constructores

[ExecutableImageOutput](#executable-image-output)

## <a name="executableimageoutput"></a><a name="executable-image-output"></a>ExecutableImageOutput

```cpp
ExecutableImageOutput(const RawEvent& event);
```

### <a name="parameters"></a>Parámetros

*Evento*\
Un evento [EXECUTABLE_IMAGE_OUTPUT.](../event-table.md#executable-image-output)

::: moniker-end
