---
title: Clase FileInput
description: Referencia C++ de la clase FILEINPUT del SDK de Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FileInput
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: bea2cf72ca2a83a9cd630f8a9ccefb87dd4b7ff1
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334851"
---
# <a name="fileinput-class"></a>Clase FileInput

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La clase `FileInput` se usa con las funciones [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)y [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Úselo para que coincida con un evento de [FILE_INPUT](../event-table.md#file-input) .

## <a name="syntax"></a>Sintaxis

```cpp
class FileInput : public SimpleEvent
{
public:
    enum class Type
    {
        OTHER               = FILE_TYPE_CODE_OTHER,
        OBJ                 = FILE_TYPE_CODE_OBJ,
        EXECUTABLE_IMAGE    = FILE_TYPE_CODE_EXECUTABLE_IMAGE,
        LIB                 = FILE_TYPE_CODE_LIB,
        IMP_LIB             = FILE_TYPE_CODE_IMP_LIB,
        EXP                 = FILE_TYPE_CODE_EXP
    };

    FileInput(const RawEvent& event);

    const wchar_t* Path() const;
    Type           Type() const;
};
```

## <a name="members"></a>Miembros

Junto con los miembros heredados de su clase base [SimpleEvent](simple-event.md) , la clase `FileInput` contiene los siguientes miembros:

### <a name="constructors"></a>Constructores

[FileInput](#file-input)

### <a name="functions"></a>Funciones

[Tipo](#type) de
de [ruta de acceso](#path)

## <a name="file-input"></a>FileInput

```cpp
FileInput(const RawEvent& event);
```

### <a name="parameters"></a>Parámetros

*event*\
Un evento de [FILE_INPUT](../event-table.md#file-input) .

## <a name="path"></a> Path

```cpp
const wchar_t Path() const;
```

### <a name="return-value"></a>Valor devuelto

Ruta de acceso absoluta al archivo de entrada.

## <a name="type"></a>Automáticamente

```cpp
Type Type() const;
```

### <a name="return-value"></a>Valor devuelto

Código que describe el tipo de archivo de entrada.

::: moniker-end
