---
title: TemplateInstantiationGroup clase
description: La referencia de clase TemplateInstantiationGroup del SDK de Compilación de C++ .
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TemplateInstantiationGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 18dd48219c7c68ce152c381eb505fe37b19ec8dd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324256"
---
# <a name="templateinstantiationgroup-class"></a>TemplateInstantiationGroup clase

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `TemplateInstantiationGroup` clase se utiliza con las funciones [MatchEventStack](../functions/match-event-stack.md) y [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Utilícelo para que coincida con grupos de [eventos de TEMPLATE_INSTANTIATION.](../event-table.md#template-instantiation)

## <a name="syntax"></a>Sintaxis

```cpp
class TemplateInstantiationGroup : public EventGroup<TemplateInstantiation>
{
public:
    TemplateInstantiationGroup(std::deque<TemplateInstantiation>&& group);
};
```

## <a name="members"></a>Miembros

Junto con los miembros heredados de su clase `TemplateInstantiationGroup` base [EventGroup\<\> TemplateInstantiation,](event-group.md) la clase contiene los siguientes miembros:

### <a name="constructors"></a>Constructores

[TemplateInstantiationGroup](#template-instantiation-group)

## <a name="templateinstantiationgroup"></a><a name="template-instantiation-group"></a>TemplateInstantiationGroup

```cpp
TemplateInstantiationGroup(std::deque<TemplateInstantiation>&& group);
```

### <a name="parameters"></a>Parámetros

*Grupo*\
Un grupo de [eventos TEMPLATE_INSTANTIATION.](../event-table.md#template-instantiation)

::: moniker-end
