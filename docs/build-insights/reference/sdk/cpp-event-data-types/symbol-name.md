---
title: Clase SymbolName
description: Referencia C++ de la clase SYMBOLNAME del SDK de Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- SymbolName
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b5e9a9b22db99c099b9f7dc1813fb335358a83e8
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334551"
---
# <a name="symbolname-class"></a>Clase SymbolName

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La clase `SymbolName` se usa con las funciones [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)y [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Úselo para que coincida con un evento de [SYMBOL_NAME](../event-table.md#symbol-name) .

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

Junto con los miembros heredados de su clase base [SimpleEvent](simple-event.md) , la clase `SymbolName` contiene los siguientes miembros:

### <a name="constructors"></a>Constructores

[SymbolName](#symbol-name)

### <a name="functions"></a>Funciones

[Nombre](#name) de la [clave](#key)


## <a name="key"></a>Clave

```cpp
const unsigned long long& Key() const;
```

### <a name="return-value"></a>Valor devuelto

Identificador numérico para el tipo representado por este símbolo. Este identificador es único dentro de una fase de front-end del compilador.

## <a name="name"></a> Name

```cpp
const char* Name() const;
```

### <a name="return-value"></a>Valor devuelto

Nombre del tipo representado por el símbolo, codificado en UTF-8.

## <a name="symbol-name"></a>SymbolName

```cpp
SymbolName(const RawEvent& event);
```

### <a name="parameters"></a>Parámetros

*event*\
Un evento de [SYMBOL_NAME](../event-table.md#symbol-name) .

::: moniker-end
