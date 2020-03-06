---
title: Clase TemplateInstantiationGroup
description: Referencia C++ de la clase TEMPLATEINSTANTIATIONGROUP del SDK de Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TemplateInstantiationGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 281088b4c6cbd39b2fb7677180a7966b490ec3ac
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334545"
---
# <a name="templateinstantiationgroup-class"></a>Clase TemplateInstantiationGroup

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La clase `TemplateInstantiationGroup` se usa con las funciones [MatchEventStack](../functions/match-event-stack.md) y [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Úselo para hacer coincidir grupos de eventos de [TEMPLATE_INSTANTIATION](../event-table.md#template-instantiation) .

## <a name="syntax"></a>Sintaxis

```cpp
class TemplateInstantiationGroup : public EventGroup<TemplateInstantiation>
{
public:
    TemplateInstantiationGroup(std::deque<TemplateInstantiation>&& group);
};
```

## <a name="members"></a>Miembros

Junto con los miembros heredados de su [EventGroup\<TemplateInstantiation\>](event-group.md) clase base, la clase `TemplateInstantiationGroup` contiene los siguientes miembros:

### <a name="constructors"></a>Constructores

[TemplateInstantiationGroup](#template-instantiation-group)

## <a name="template-instantiation-group"></a>TemplateInstantiationGroup

```cpp
TemplateInstantiationGroup(std::deque<TemplateInstantiation>&& group);
```

### <a name="parameters"></a>Parámetros

\ de *Grupo*
Grupo de eventos de [TEMPLATE_INSTANTIATION](../event-table.md#template-instantiation) .

::: moniker-end
