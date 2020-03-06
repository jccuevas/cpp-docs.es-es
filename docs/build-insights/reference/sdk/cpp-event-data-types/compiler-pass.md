---
title: Clase CompilerPass
description: Referencia C++ de la clase COMPILERPASS del SDK de Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CompilerPass
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 3c2fa1c2c4be8aaf5bec77b383f93a4b033ca8e3
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334959"
---
# <a name="compilerpass-class"></a>Clase CompilerPass

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La clase `CompilerPass` se usa con las funciones [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)y [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Úselo para que coincida con un evento [BACK_END_PASS](../event-table.md#back-end-pass) o [FRONT_END_PASS](../event-table.md#front-end-pass) .

## <a name="syntax"></a>Sintaxis

```cpp
class CompilerPass : public Activity
{
public:
    enum class PassCode
    {
        FRONT_END,
        BACK_END
    };

    CompilerPass(const RawEvent& event);

    PassCode       PassCode() const;
    const wchar_t* InputSourcePath() const;
    const wchar_t* OutputObjectPath() const;
};
```

## <a name="members"></a>Miembros

Junto con los miembros heredados de su clase base de [actividad](activity.md) , la clase `CompilerPass` contiene los siguientes miembros:

### <a name="constructors"></a>Constructores

[CompilerPass](#compiler-pass)

### <a name="enums"></a>Enumeraciones

#### <a name="passcode"></a>Restablecimiento

|||
|-|-|
|FRONT_END|El paso front-end.|
|BACK_END|La fase de back-end.|

### <a name="functions"></a>Funciones

\ [InputSourcePath](#input-source-path)
\ [OutputObjectPath](#output-object-path)
\ de [código](#pass-code) de acceso

## <a name="compiler-pass"></a>CompilerPass

```cpp
CompilerPass(const RawEvent& event);
```

### <a name="parameters"></a>Parámetros

*event*\
[BACK_END_PASS](../event-table.md#back-end-pass) o [FRONT_END_PASS](../event-table.md#front-end-pass) evento.

## <a name="input-source-path"></a>InputSourcePath

```cpp
const wchar_t* InputSourcePath() const;
```

### <a name="return-value"></a>Valor devuelto

Ruta de acceso absoluta al archivo de origen de entrada procesado por este paso del compilador.

## <a name="output-object-path"></a>OutputObjectPath

```cpp
const wchar_t* OutputObjectPath() const;
```

### <a name="return-value"></a>Valor devuelto

Ruta de acceso absoluta al archivo de objeto de salida generado por este paso del compilador.

## <a name="pass-code"></a>Restablecimiento

```cpp
PassCode PassCode() const;
```

### <a name="return-value"></a>Valor devuelto

Un código que indica qué paso del compilador se representa mediante este objeto CompilerPass.

::: moniker-end
