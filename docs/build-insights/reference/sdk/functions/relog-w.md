---
title: RelogW
description: Referencia de la función RelogW del SDK de C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RelogW
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c5d5f6e35c7cd24d2324ce1d8a0434d9048b1d85
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323812"
---
# <a name="relogw"></a>RelogW

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `RelogW` función se utiliza para leer eventos MSVC desde un seguimiento de seguimiento de eventos para Windows (ETW) de entrada y escribirlos en un nuevo seguimiento ETW modificado.

## <a name="syntax"></a>Sintaxis

```cpp
enum RESULT_CODE RelogW(
    const wchar_t*          inputLogFile,
    const wchar_t*          outputLogFile,
    const RELOG_DESCRIPTOR* relogDescriptor);
```

### <a name="parameters"></a>Parámetros

*inputLogFile*\
El seguimiento ETW de entrada desde el que desea leer eventos.

*outputLogFile*\
El archivo en el que se escribiron los nuevos eventos.

*relogDescriptor*\
Puntero a un objeto [RELOG_DESCRIPTOR.](../other-types/relog-descriptor-struct.md) Utilice este objeto para configurar la sesión de recorrección.

### <a name="return-value"></a>Valor devuelto

Un código de resultado de la [enumeración de RESULT_CODE.](../other-types/result-code-enum.md)

::: moniker-end
