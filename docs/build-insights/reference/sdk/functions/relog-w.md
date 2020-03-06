---
title: RelogW
description: La C++ referencia de la función RELOGW del SDK de Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RelogW
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 563b1aa92877ff5bc1216bc914c1c661de06dfc0
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334293"
---
# <a name="relogw"></a>RelogW

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La función `RelogW` se usa para leer eventos MSVC desde un seguimiento de seguimiento de eventos de entrada para Windows (ETW) y escribirlos en un seguimiento ETW nuevo y modificado.

## <a name="syntax"></a>Sintaxis

```cpp
enum RESULT_CODE RelogW(
    const wchar_t*          inputLogFile,
    const wchar_t*          outputLogFile,
    const RELOG_DESCRIPTOR* relogDescriptor);
```

### <a name="parameters"></a>Parámetros

\ *inputLogFile*
Seguimiento de ETW de entrada del que desea leer eventos.

\ *outputLogFile*
Archivo en el que se van a escribir los nuevos eventos.

\ *relogDescriptor*
Puntero a un objeto de [RELOG_DESCRIPTOR](../other-types/relog-descriptor-struct.md) . Utilice este objeto para configurar la sesión de registro.

### <a name="return-value"></a>Valor devuelto

Código de resultado de la enumeración [RESULT_CODE](../other-types/result-code-enum.md) .

::: moniker-end
