---
title: Clase SymbolName
description: La referencia de clase SymbolName del SDK de Compilación de C++.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- SymbolName
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1306fb43d6c2140a75b36c5f142532916cf26ae4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324352"
---
# <a name="symbolname-class"></a>Clase SymbolName

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `SymbolName` clase se utiliza con las funciones [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)y [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilícelo para que coincida con un evento [SYMBOL_NAME.](../event-table.md#symbol-name)

## <a name="syntax"></a>Sintaxis

```cpp
class SymbolName : public SimpleEvent
{
public:
    SymbolName(const RawEvent& event);

    const unsigned long long&  Key() const;
    const char*                Name() const;
};
```

## <a name="members"></a>Miembros

Junto con los miembros heredados de `SymbolName` su clase base [SimpleEvent,](simple-event.md) la clase contiene los siguientes miembros:

### <a name="constructors"></a>Constructores

[SymbolName](#symbol-name)

### <a name="functions"></a>Functions

[Nombre](#key)
[clave](#name)

## <a name="key"></a><a name="key"></a>Clave

```cpp
const unsigned long long& Key() const;
```

### <a name="return-value"></a>Valor devuelto

Identificador numérico del tipo representado por este símbolo. Este identificador es único dentro de un paso de front-end del compilador.

## <a name="name"></a><a name="name"></a>Nombre

```cpp
const char* Name() const;
```

### <a name="return-value"></a>Valor devuelto

El nombre del tipo representado por el símbolo, codificado en UTF-8.

## <a name="symbolname"></a><a name="symbol-name"></a>SymbolName

```cpp
SymbolName(const RawEvent& event);
```

### <a name="parameters"></a>Parámetros

*Evento*\
Un [evento SYMBOL_NAME.](../event-table.md#symbol-name)

::: moniker-end
