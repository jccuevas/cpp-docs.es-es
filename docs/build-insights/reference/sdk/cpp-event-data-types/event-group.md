---
title: Clase EventGroup
description: La referencia de clase EventGroup del SDK de Compilación de C++ .
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EventGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 596c18ca0e9b4d7b26c4ed5209b16871952c4af2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324984"
---
# <a name="eventgroup-class"></a>Clase EventGroup

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

La `EventGroup` plantilla de clase es la clase base para todas las clases de captura de grupo.

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

*TActivity* El tipo de actividad contenido en el grupo.

## <a name="members"></a>Miembros

### <a name="functions"></a>Functions

[Back](#back)
[begin](#begin)
[end](#end)
Operador[delantero[]](#subscript-operator)
[Front](#front)
[Tamaño](#size)

## <a name="back"></a><a name="back"></a>Atrás

```cpp
const TActivity& Back() const;
```

### <a name="return-value"></a>Valor devuelto

Una referencia al último evento de actividad del grupo.

## <a name="begin"></a><a name="begin"></a>Comenzar

```cpp
std::deque<TActivity>::const_iterator begin() const;
```

### <a name="return-value"></a>Valor devuelto

Un iterador que apunta al principio del grupo de eventos de actividad.

## <a name="end"></a><a name="end"></a>Final

```cpp
std::deque<TActivity>::const_iterator end() const;
```

### <a name="return-value"></a>Valor devuelto

Iterador que indica una posición más allá del final del grupo de eventos de actividad.

## <a name="front"></a><a name="front"></a>Frente

```cpp
const TActivity& Front() const;
```

### <a name="return-value"></a>Valor devuelto

Una referencia al primer evento de actividad del grupo.

## <a name="operator"></a><a name="subscript-operator"></a>operador[]

```cpp
const TActivity& operator[](size_t index) const;
```

### <a name="parameters"></a>Parámetros

*Índice*\
El índice del elemento al que se va a tener acceso en el grupo de eventos de actividad.

### <a name="return-value"></a>Valor devuelto

El evento de la pila de eventos almacenada en la posición indicada por *index*.

## <a name="size"></a>Tamaño de la <a name="size"></a>

```cpp
size_t Size() const;
```

### <a name="return-value"></a>Valor devuelto

El tamaño del grupo de eventos.

::: moniker-end
