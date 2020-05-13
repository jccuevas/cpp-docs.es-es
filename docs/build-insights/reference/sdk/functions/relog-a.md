---
title: RelogA
description: Referencia de la función RelogA del SDK de C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RelogA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 5a772b1156fc69eeef39514afe401c549c3b7c38
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323849"
---
# <a name="reloga"></a>RelogA

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `RelogA` función se utiliza para leer eventos MSVC de un seguimiento de seguimiento de eventos para Windows (ETW) y escribirlos en un nuevo seguimiento ETW modificado.

## <a name="syntax"></a>Sintaxis

```cpp
enum RESULT_CODE RelogA(
    const char*             inputLogFile,
    const char*             outputLogFile,
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
