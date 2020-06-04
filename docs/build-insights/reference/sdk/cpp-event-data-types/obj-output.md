---
title: Clase ObjOutput
description: La referencia de clase ObjOutput del SDK de Compilación de C++.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ObjOutput
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 194253e8995401114e2529b868b36c9823510a4f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324492"
---
# <a name="objoutput-class"></a>Clase ObjOutput

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `ObjOutput` clase se utiliza con las funciones [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)y [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilícelo para que coincida con un evento [OBJ_OUTPUT.](../event-table.md#obj-output)

## <a name="syntax"></a>Sintaxis

```cpp
class ObjOutput : public FileOutput
{
public:
    ObjOutput(const RawEvent& event);
};
```

## <a name="members"></a>Miembros

Junto con los miembros heredados de `ObjOutput` su clase base [FileOutput,](file-output.md) la clase contiene los siguientes miembros:

### <a name="constructors"></a>Constructores

[ObjOutput](#obj-output)

## <a name="objoutput"></a><a name="obj-output"></a>ObjOutput

```cpp
ObjOutput(const RawEvent& event);
```

### <a name="parameters"></a>Parámetros

*Evento*\
Un evento [OBJ_OUTPUT.](../event-table.md#obj-output)

::: moniker-end
