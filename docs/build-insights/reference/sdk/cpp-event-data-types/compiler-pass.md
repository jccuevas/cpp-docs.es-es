---
title: Clase CompilerPass
description: La referencia de clase CompilerPass del SDK de C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CompilerPass
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 11af981b647d5183f88dad024d90c0ef4f8a28bc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325040"
---
# <a name="compilerpass-class"></a>Clase CompilerPass

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `CompilerPass` clase se utiliza con las funciones [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)y [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilícelo para que coincida con un evento [BACK_END_PASS](../event-table.md#back-end-pass) o [FRONT_END_PASS.](../event-table.md#front-end-pass)

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

Junto con los miembros heredados `CompilerPass` de su clase base [Activity,](activity.md) la clase contiene los siguientes miembros:

### <a name="constructors"></a>Constructores

[CompilerPass](#compiler-pass)

### <a name="enums"></a>Enumeraciones

#### <a name="passcode"></a>Contraseña

|||
|-|-|
|FRONT_END|El pase de primera línea.|
|BACK_END|El pase de back-end.|

### <a name="functions"></a>Functions

[InputSourcePath](#input-source-path)\
[OutputObjectPath](#output-object-path)\
[Contraseña](#pass-code)\

## <a name="compilerpass"></a><a name="compiler-pass"></a>CompilerPass

```cpp
CompilerPass(const RawEvent& event);
```

### <a name="parameters"></a>Parámetros

*Evento*\
Un [evento BACK_END_PASS](../event-table.md#back-end-pass) o [FRONT_END_PASS.](../event-table.md#front-end-pass)

## <a name="inputsourcepath"></a><a name="input-source-path"></a>InputSourcePath

```cpp
const wchar_t* InputSourcePath() const;
```

### <a name="return-value"></a>Valor devuelto

La ruta de acceso absoluta al archivo de origen de entrada procesado por este paso del compilador.

## <a name="outputobjectpath"></a><a name="output-object-path"></a>OutputObjectPath

```cpp
const wchar_t* OutputObjectPath() const;
```

### <a name="return-value"></a>Valor devuelto

La ruta de acceso absoluta al archivo de objeto de salida generado por este paso del compilador.

## <a name="passcode"></a><a name="pass-code"></a>Contraseña

```cpp
PassCode PassCode() const;
```

### <a name="return-value"></a>Valor devuelto

Código que indica qué paso del compilador se representa mediante este compilerPass objeto.

::: moniker-end
