---
title: EventTargetArray (Clase)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::EventTargetArray
- event/Microsoft::WRL::Details::EventTargetArray::AddTail
- event/Microsoft::WRL::Details::EventTargetArray::Begin
- event/Microsoft::WRL::Details::EventTargetArray::End
- event/Microsoft::WRL::Details::EventTargetArray::EventTargetArray
- event/Microsoft::WRL::Details::EventTargetArray::Length
- event/Microsoft::WRL::Details::EventTargetArray::~EventTargetArray
helpviewer_keywords:
- Microsoft::WRL::Details::EventTargetArray class
- Microsoft::WRL::Details::EventTargetArray::AddTail method
- Microsoft::WRL::Details::EventTargetArray::Begin method
- Microsoft::WRL::Details::EventTargetArray::End method
- Microsoft::WRL::Details::EventTargetArray::EventTargetArray, constructor
- Microsoft::WRL::Details::EventTargetArray::Length method
- Microsoft::WRL::Details::EventTargetArray::~EventTargetArray, destructor
ms.assetid: e3cadb7c-2160-4cbb-a2f8-c28733d1e96d
ms.openlocfilehash: 9ea8800aa22a6b5cae0b3342cf337786fb53fc76
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371500"
---
# <a name="eventtargetarray-class"></a>EventTargetArray (Clase)

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
class EventTargetArray :
    public Microsoft::WRL::RuntimeClass<
        Microsoft::WRL::RuntimeClassFlags<ClassicCom>,
        IUnknown
    >;
```

## <a name="remarks"></a>Observaciones

Representa una matriz de controladores de eventos.

Los controladores de eventos que están asociados con `EventTargetArray` un [EventSource](eventsource-class.md) objeto se almacenan en un miembro de datos protegido.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

Nombre                                                           | Descripción
-------------------------------------------------------------- | -----------------------------------------------------------
[EventTargetArray::EventTargetArray](#eventtargetarray)        | Inicializa una nueva instancia de la clase `EventTargetArray`.
[EventTargetArray::-EventTargetArray](#tilde-eventtargetarray) | Desinicializa la `EventTargetArray` clase actual.

### <a name="public-methods"></a>Métodos públicos

Nombre                                  | Descripción
------------------------------------- | ---------------------------------------------------------------------------------------
[EventTargetArray::AddTail](#addtail) | Anexa el controlador de eventos especificado al final de la matriz interna de controladores de eventos.
[EventTargetArray::Begin](#begin)     | Obtiene la dirección del primer elemento de la matriz interna de controladores de eventos.
[EventTargetArray::End](#end)         | Obtiene la dirección del último elemento de la matriz interna de controladores de eventos.
[EventTargetArray::Longitud](#length)   | Obtiene el número actual de elementos de la matriz interna de controladores de eventos.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`EventTargetArray`

## <a name="requirements"></a>Requisitos

**Encabezado:** event.h

**Espacio de nombres:** Microsoft::WRL::Details

## <a name="eventtargetarrayeventtargetarray"></a><a name="tilde-eventtargetarray"></a>EventTargetArray::-EventTargetArray

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

```cpp
~EventTargetArray();
```

### <a name="remarks"></a>Observaciones

Desinicializa la `EventTargetArray` clase actual.

## <a name="eventtargetarrayaddtail"></a><a name="addtail"></a>EventTargetArray::AddTail

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

```cpp
void AddTail(
   _In_ IUnknown* element
);
```

### <a name="parameters"></a>Parámetros

*Elemento*<br/>
Puntero al controlador de eventos que se va a anexar.

### <a name="remarks"></a>Observaciones

Anexa el controlador de eventos especificado al final de la matriz interna de controladores de eventos.

`AddTail()`está destinado a ser utilizado `EventSource` internamente sólo por la clase.

## <a name="eventtargetarraybegin"></a><a name="begin"></a>EventTargetArray::Begin

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

```cpp
ComPtr<IUnknown>* Begin();
```

### <a name="return-value"></a>Valor devuelto

La dirección del primer elemento de la matriz interna de controladores de eventos.

### <a name="remarks"></a>Observaciones

Obtiene la dirección del primer elemento de la matriz interna de controladores de eventos.

## <a name="eventtargetarrayend"></a><a name="end"></a>EventTargetArray::End

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

```cpp
ComPtr<IUnknown>* End();
```

### <a name="return-value"></a>Valor devuelto

La dirección del último elemento de la matriz interna de controladores de eventos.

### <a name="remarks"></a>Observaciones

Obtiene la dirección del último elemento de la matriz interna de controladores de eventos.

## <a name="eventtargetarrayeventtargetarray"></a><a name="eventtargetarray"></a>EventTargetArray::EventTargetArray

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

```cpp
EventTargetArray(
   _Out_ HRESULT* hr,
   size_t items
);
```

### <a name="parameters"></a>Parámetros

*Hr*<br/>
Después de estas operaciones de constructor, el parámetro *hr* indica si la asignación de la matriz se realizó correctamente o no. La lista siguiente muestra los valores posibles para *hr*.

- S_OK<br/>
  La operación se realizó correctamente.

- E_OUTOFMEMORY<br/>
  No se pudo asignar memoria para la matriz.

- S_FALSE<br/>
  Los *elementos* de parámetro son menores o iguales que cero.

*Artículos*<br/>
El número de elementos de matriz que se va a asignar.

### <a name="remarks"></a>Observaciones

Inicializa una nueva instancia de la clase `EventTargetArray`.

`EventTargetArray`se utiliza para mantener una matriz `EventSource` de controladores de eventos en un objeto.

## <a name="eventtargetarraylength"></a><a name="length"></a>EventTargetArray::Longitud

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

```cpp
size_t Length();
```

### <a name="return-value"></a>Valor devuelto

El número actual de elementos de la matriz interna de controladores de eventos.

### <a name="remarks"></a>Observaciones

Obtiene el número actual de elementos de la matriz interna de controladores de eventos.
