---
title: MakeDynamicReloggerGroup
description: La C++ referencia de la función MAKEDYNAMICRELOGGERGROUP del SDK de Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeDynamicReloggerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 4ad394d3ba2982e7ee4f2a497fef2ea65a3c1769
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334401"
---
# <a name="makedynamicreloggergroup"></a>MakeDynamicReloggerGroup

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La función `MakeDynamicReloggerGroup` se usa para crear un grupo de registro dinámico. Los miembros de un grupo de reregistradores reciben los eventos uno por uno de izquierda a derecha hasta que se hayan procesado todos los eventos de un seguimiento.

## <a name="syntax"></a>Sintaxis

```cpp
auto MakeDynamicReloggerGroup(std::vector<IRelogger*> reloggers);

auto MakeDynamicReloggerGroup(std::vector<std::shared_ptr<IRelogger>> reloggers);

auto MakeDynamicReloggerGroup(std::vector<std::unique_ptr<IRelogger>> reloggers);
```

### <a name="parameters"></a>Parámetros

\ de los *registradores*
Vector de punteros [IRelogger](../other-types/irelogger-class.md) incluido en el grupo de registro dinámico. Estos punteros pueden ser RAW, `std::unique_ptr`o `std::shared_ptr`. Los punteros [IAnalyzer](../other-types/ianalyzer-class.md) también se consideran punteros `IRelogger` a causa de una relación de herencia.

### <a name="return-value"></a>Valor devuelto

Un grupo de registro dinámico. Use la palabra clave **auto** para capturar el valor devuelto.

## <a name="remarks"></a>Comentarios

A diferencia de los grupos de reregistradores estáticos, los miembros de un grupo de registro dinámico no necesitan conocerse en tiempo de compilación. Puede elegir miembros del grupo de reregistrador en tiempo de ejecución en función de la entrada del programa o en función de otros valores desconocidos en tiempo de compilación. A diferencia de los grupos de reregistradores estáticos, los punteros de [IRelogger](../other-types/irelogger-class.md) dentro de un grupo de registro dinámico tienen un comportamiento polimórfico y las llamadas a funciones virtuales se envían correctamente. Esta flexibilidad se produce a costa de un tiempo de procesamiento de eventos posiblemente más lento. Cuando todos los miembros del grupo de registro se conocen en tiempo de compilación, y si no necesita un comportamiento polimórfico, considere la posibilidad de usar un grupo de registradores estáticos. Para usar un grupo de reregistradores estáticos, llame a [MakeStaticReloggerGroup](make-static-relogger-group.md) en su lugar.

Un grupo de registradores dinámicos se puede encapsular dentro de un grupo de registro estático. La dirección se pasa a [MakeStaticReloggerGroup](make-static-relogger-group.md). Utilice esta técnica para pasar grupos de registradores dinámicos a funciones como [relog](relog.md), que solo aceptan grupos de reregistradores estáticos.

::: moniker-end
