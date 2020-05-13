---
title: Clase FileOutput
description: La referencia de clase FileOutput del SDK de C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FileOutput
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 37823da8a4aaac0ce4094583b8aee8ac1eb04aaa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324810"
---
# <a name="fileoutput-class"></a>Clase FileOutput

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `FileOutput` clase se utiliza con las funciones [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)y [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilícelo para que coincida con un evento [EXECUTABLE_IMAGE_OUTPUT](../event-table.md#executable-image-output), [EXP_OUTPUT](../event-table.md#exp-output), [IMP_LIB_OUTPUT](../event-table.md#imp-lib-output), [LIB_OUTPUT](../event-table.md#lib-output)o [OBJ_OUTPUT.](../event-table.md#obj-output)

## <a name="syntax"></a>Sintaxis

```cpp
class FileOutput : public SimpleEvent
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

    FileOutput(const RawEvent& event);

    const wchar_t* Path() const;
    Type           Type() const;
};
```

## <a name="members"></a>Miembros

Junto con los miembros heredados de `FileOutput` su clase base [SimpleEvent,](simple-event.md) la clase contiene los siguientes miembros:

### <a name="constructors"></a>Constructores

[FileOutput](#file-output)

### <a name="functions"></a>Functions

[Path](#path)
[Tipo](#type) de ruta

## <a name="fileoutput"></a><a name="file-output"></a>FileOutput

```cpp
FileOutput(const RawEvent& event);
```

### <a name="parameters"></a>Parámetros

*Evento*\
Un evento [EXECUTABLE_IMAGE_OUTPUT](../event-table.md#executable-image-output), [EXP_OUTPUT](../event-table.md#exp-output), [IMP_LIB_OUTPUT](../event-table.md#imp-lib-output), [LIB_OUTPUT](../event-table.md#lib-output)o [OBJ_OUTPUT.](../event-table.md#obj-output)

## <a name="path"></a><a name="path"></a>Camino

```cpp
const wchar_t Path() const;
```

### <a name="return-value"></a>Valor devuelto

La ruta de acceso absoluta al archivo de salida.

## <a name="type"></a>Tipo de <a name="type"></a>

```cpp
Type Type() const;
```

### <a name="return-value"></a>Valor devuelto

Código que describe el tipo de archivo de salida.

::: moniker-end
