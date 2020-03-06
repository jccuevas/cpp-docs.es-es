---
title: MakeStaticReloggerGroup
description: La C++ referencia de la función MAKESTATICRELOGGERGROUP del SDK de Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeStaticReloggerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 06927af89b16d9de1148e555868dd2022c59b171
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334389"
---
# <a name="makestaticreloggergroup"></a>MakeStaticReloggerGroup

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La función `MakeStaticReloggerGroup` se usa para crear un grupo de registradores estáticos que se puede pasar a funciones como [relog](relog.md). Los miembros de un grupo de reregistradores reciben los eventos uno por uno de izquierda a derecha hasta que se hayan procesado todos los eventos de un seguimiento.

## <a name="syntax"></a>Sintaxis

```cpp
template <typename... TReloggerPtrs>
auto MakeStaticReloggerGroup(TReloggerPtrs... reloggers);
```

### <a name="parameters"></a>Parámetros

\ *TReloggerPtrs*
Este parámetro siempre se deduce.

\ de los *registradores*
Un paquete de parámetros de punteros [IRelogger](../other-types/irelogger-class.md) que se incluye en el grupo de registro estático. Estos punteros pueden ser RAW, `std::unique_ptr`o `std::shared_ptr`. Los punteros [IAnalyzer](../other-types/ianalyzer-class.md) también se consideran punteros `IRelogger` a causa de una relación de herencia.

### <a name="return-value"></a>Valor devuelto

Un grupo de registradores estáticos. Use la palabra clave **auto** para capturar el valor devuelto.

## <a name="remarks"></a>Comentarios

A diferencia de los grupos de registro dinámico, los miembros de un grupo de reregistradores estáticos deben conocerse en tiempo de compilación. Además, un grupo de reregistradores estáticos contiene punteros [IRelogger](../other-types/irelogger-class.md) que no tienen un comportamiento polimórfico. Cuando se usa un grupo de reregistradores estáticos para analizar un seguimiento de seguimiento de eventos para Windows (ETW), las llamadas a la interfaz `IRelogger` siempre se resuelven en el objeto al que apunta directamente el miembro del grupo de reregistrador. Esta pérdida de flexibilidad viene con la posibilidad de tiempos de procesamiento de eventos más rápidos. Si los miembros de un grupo de reregistrador no se pueden conocer en tiempo de compilación, o si necesita un comportamiento polimórfico en los punteros de `IRelogger`, considere la posibilidad de usar un grupo de registro dinámico. Puede usar un grupo de registradores dinámicos llamando a [MakeDynamicReloggerGroup](make-dynamic-relogger-group.md) en su lugar.

::: moniker-end
