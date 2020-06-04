---
title: MakeStaticReloggerGroup
description: Referencia de la función MakeStaticReloggerGroup del SDK de Compilación de C++ .
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeStaticReloggerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 75b638537cb8e0cdeeb5476a3f5277e8e90d9baf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323915"
---
# <a name="makestaticreloggergroup"></a>MakeStaticReloggerGroup

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `MakeStaticReloggerGroup` función se utiliza para crear un grupo de reregistrador estático que se puede pasar a funciones como [Relog](relog.md). Los miembros de un grupo de registrador es dores de eventos uno por uno de izquierda a derecha hasta que se han procesado todos los eventos de un seguimiento.

## <a name="syntax"></a>Sintaxis

```cpp
template <typename... TReloggerPtrs>
auto MakeStaticReloggerGroup(TReloggerPtrs... reloggers);
```

### <a name="parameters"></a>Parámetros

*TReloggerPtrs*\
Este parámetro siempre se deduce.

*reloggers*\
Un paquete de parámetros de punteros [IRelogger](../other-types/irelogger-class.md) que se incluye en el grupo de registrador estático. Estos punteros pueden `std::unique_ptr`ser `std::shared_ptr`sin procesar, , o . [Los](../other-types/ianalyzer-class.md) punteros IAnalyzer `IRelogger` también se consideran punteros debido a una relación de herencia.

### <a name="return-value"></a>Valor devuelto

Un grupo de reregistrador estático. Utilice la palabra clave **auto** para capturar el valor devuelto.

## <a name="remarks"></a>Observaciones

A diferencia de los grupos de reregistrador dinámicos, los miembros de un grupo de reregistrador estático deben conocerse en tiempo de compilación. Además, un grupo de reregistrador estático contiene punteros [IRelogger](../other-types/irelogger-class.md) que no tienen un comportamiento polimórfico. Cuando se utiliza un grupo de reregistrador estático para analizar un `IRelogger` seguimiento de seguimiento de eventos para Windows (ETW), las llamadas a la interfaz siempre se resuelven en el objeto al que apunta directamente el miembro del grupo de registrador. Esta pérdida de flexibilidad viene con la posibilidad de tiempos de procesamiento de eventos más rápidos. Si los miembros de un grupo de reregistradores no se pueden conocer `IRelogger` en tiempo de compilación, o si necesita un comportamiento polimórfico en los punteros, considere la posibilidad de usar un grupo de reregistrador dinámico. Puede usar un grupo de reregistrador dinámico llamando a [MakeDynamicReloggerGroup](make-dynamic-relogger-group.md) en su lugar.

::: moniker-end
