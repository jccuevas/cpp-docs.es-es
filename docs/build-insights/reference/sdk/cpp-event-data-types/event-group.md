---
title: Clase EventGroup
description: Referencia C++ de la clase EVENTGROUP del SDK de Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EventGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ac8ac70f3fc160714b86dd0c483808a4d06e7699
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334923"
---
# <a name="eventgroup-class"></a>Clase EventGroup

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La plantilla de clase `EventGroup` es la clase base para todas las clases de captura de grupo.

## <a name="syntax"></a>Sintaxis

```cpp
template <typename TActivity>
class EventGroup;
{
public:
    size_t Size() const;

    const TActivity& operator[](size_t index) const;
    const TActivity& Front() const;
    const TActivity& Back() const;

    std::deque<TActivity>::const_iterator begin() const;
    std::deque<TActivity>::const_iterator end() const;
};
```

### <a name="parameters"></a>Parámetros

*TActivity* Tipo de actividad contenido en el grupo.

## <a name="members"></a>Miembros

### <a name="functions"></a>Funciones

[Atrás](#back)
[iniciar](#begin)
[final](#end)
[Front](#front)
[Operator []](#subscript-operator)
[tamaño](#size)

## <a name="back"></a>Atrás

```cpp
const TActivity& Back() const;
```

### <a name="return-value"></a>Valor devuelto

Referencia al último evento de actividad del grupo.

## <a name="begin"></a>inicia

```cpp
std::deque<TActivity>::const_iterator begin() const;
```

### <a name="return-value"></a>Valor devuelto

Iterador que apunta al principio del grupo de eventos de actividad.

## <a name="end"></a>extremo

```cpp
std::deque<TActivity>::const_iterator end() const;
```

### <a name="return-value"></a>Valor devuelto

Iterador que apunta a una posición después del final del grupo de eventos de actividad.

## <a name="front"></a>End

```cpp
const TActivity& Front() const;
```

### <a name="return-value"></a>Valor devuelto

Referencia al primer evento de actividad del grupo.

## <a name="subscript-operator"></a>operador []

```cpp
const TActivity& operator[](size_t index) const;
```

### <a name="parameters"></a>Parámetros

*índice*\
Índice del elemento al que se va a obtener acceso en el grupo de eventos de actividad.

### <a name="return-value"></a>Valor devuelto

Evento de la pila de eventos almacenado en la posición indicada por el *Índice*.

## <a name="size"></a>Ajusta

```cpp
size_t Size() const;
```

### <a name="return-value"></a>Valor devuelto

Tamaño del grupo de eventos.

::: moniker-end
