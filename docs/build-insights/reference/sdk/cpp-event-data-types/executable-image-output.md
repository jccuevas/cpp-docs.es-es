---
title: Clase ExecutableImageOutput
description: Referencia C++ de la clase EXECUTABLEIMAGEOUTPUT del SDK de Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ExecutableImageOutput
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 5a2e417a7dd976f257b4dd5a3aabfdf440c604fc
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334881"
---
# <a name="executableimageoutput-class"></a>Clase ExecutableImageOutput

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La clase `ExecutableImageOutput` se usa con las funciones [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)y [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Úselo para que coincida con un evento de [EXECUTABLE_IMAGE_OUTPUT](../event-table.md#executable-image-output) .

## <a name="syntax"></a>Sintaxis

```cpp
class ExecutableImageOutput : public FileOutput
{
public:
    ExecutableImageOutput(const RawEvent& event);
};
```

## <a name="members"></a>Miembros

Junto con los miembros heredados de su clase base [FileOutput](file-output.md) , la clase `ExecutableImageOutput` contiene los siguientes miembros:

### <a name="constructors"></a>Constructores

[ExecutableImageOutput](#executable-image-output)

## <a name="executable-image-output"></a>ExecutableImageOutput

```cpp
ExecutableImageOutput(const RawEvent& event);
```

### <a name="parameters"></a>Parámetros

*event*\
Un evento de [EXECUTABLE_IMAGE_OUTPUT](../event-table.md#executable-image-output) .

::: moniker-end
