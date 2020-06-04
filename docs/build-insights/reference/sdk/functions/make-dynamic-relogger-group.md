---
title: MakeDynamicReloggerGroup
description: Referencia de la función MakeDynamicReloggerGroup del SDK de Compilación de C++ .
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeDynamicReloggerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: f49e37f8e1a8b9ca9a800d20b2891a54453095ef
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323951"
---
# <a name="makedynamicreloggergroup"></a>MakeDynamicReloggerGroup

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `MakeDynamicReloggerGroup` función se utiliza para crear un grupo de reregistrador dinámico. Los miembros de un grupo de registrador es dores de eventos uno por uno de izquierda a derecha hasta que se han procesado todos los eventos de un seguimiento.

## <a name="syntax"></a>Sintaxis

```cpp
auto MakeDynamicReloggerGroup(std::vector<IRelogger*> reloggers);

auto MakeDynamicReloggerGroup(std::vector<std::shared_ptr<IRelogger>> reloggers);

auto MakeDynamicReloggerGroup(std::vector<std::unique_ptr<IRelogger>> reloggers);
```

### <a name="parameters"></a>Parámetros

*reloggers*\
Un vector de punteros [IRelogger](../other-types/irelogger-class.md) incluidos en el grupo de reregistrador dinámico. Estos punteros pueden `std::unique_ptr`ser `std::shared_ptr`sin procesar, , o . [Los](../other-types/ianalyzer-class.md) punteros IAnalyzer `IRelogger` también se consideran punteros debido a una relación de herencia.

### <a name="return-value"></a>Valor devuelto

Un grupo de relogger dinámico. Utilice la palabra clave **auto** para capturar el valor devuelto.

## <a name="remarks"></a>Observaciones

A diferencia de los grupos de reregistrador estáticos, los miembros de un grupo de reregistrador dinámico no necesitan ser conocidos en tiempo de compilación. Puede elegir miembros del grupo de reregistrador en tiempo de ejecución en función de la entrada del programa o en función de otros valores desconocidos en tiempo de compilación. A diferencia de los grupos de reregistrador estáticos, los punteros [IRelogger](../other-types/irelogger-class.md) dentro de un grupo de reregistrador dinámico tienen un comportamiento polimórfico y las llamadas a funciones virtuales se distribuyen correctamente. Esta flexibilidad se obtiene a costa de un tiempo de procesamiento de eventos posiblemente más lento. Cuando todos los miembros del grupo de registrador se conocen en tiempo de compilación y si no necesita un comportamiento polimórfico, considere la posibilidad de usar un grupo de registrador estático. Para utilizar un grupo de reregistrador estático, llame a [MakeStaticReloggerGroup](make-static-relogger-group.md) en su lugar.

Un grupo de relogger dinámico se puede encapsular dentro de un grupo de relogger estático. Pasa su dirección a [MakeStaticReloggerGroup](make-static-relogger-group.md). Utilice esta técnica para pasar grupos de reregistrador dinámicos a funciones como [Relog](relog.md), que solo aceptan grupos de registrador estáticos.

::: moniker-end
