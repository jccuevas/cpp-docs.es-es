---
title: Clase de función
description: La referencia de clase Function del SDK de C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Function
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 69acbe4d6630de37120aec89a24a9f33d447009e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324722"
---
# <a name="function-class"></a>Clase de función

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `Function` clase se utiliza con las funciones [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)y [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilícelo para que coincida con un evento [FUNCTION.](../event-table.md#function)

## <a name="syntax"></a>Sintaxis

```cpp
class Function : public Activity
{
public:
    Function(const RawEvent& event);

    const char* Name() const;
};
```

## <a name="members"></a>Miembros

Junto con los miembros heredados `Function` de su clase base [Activity,](activity.md) la clase contiene los siguientes miembros:

### <a name="constructors"></a>Constructores

[Función](#function)

### <a name="functions"></a>Functions

[Nombre](#name)

## <a name="function"></a><a name="function"></a>Función

```cpp
Function(const RawEvent& event);
```

### <a name="parameters"></a>Parámetros

*Evento*\
Un evento [FUNCTION.](../event-table.md#function)

## <a name="name"></a><a name="name"></a>Nombre

```cpp
const char* Name() const;
```

### <a name="return-value"></a>Valor devuelto

El nombre de la función, codificado en UTF-8.

::: moniker-end
