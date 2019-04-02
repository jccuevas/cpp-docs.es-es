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
ms.openlocfilehash: 1f3f8e299dba1f4b6ae5a5767f11989dc2fe8370
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58785781"
---
# <a name="eventtargetarray-class"></a>EventTargetArray (Clase)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
class EventTargetArray :
    public Microsoft::WRL::RuntimeClass<
        Microsoft::WRL::RuntimeClassFlags<ClassicCom>,
        IUnknown
    >;
```

## <a name="remarks"></a>Comentarios

Representa una matriz de controladores de eventos.

Los controladores de eventos que están asociados con un [EventSource](eventsource-class.md) objeto se almacenan en un protegido `EventTargetArray` miembro de datos.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

Name                                                           | Descripción
-------------------------------------------------------------- | -----------------------------------------------------------
[EventTargetArray::EventTargetArray](#eventtargetarray)        | Inicializa una nueva instancia de la clase `EventTargetArray`.
[EventTargetArray::~EventTargetArray](#tilde-eventtargetarray) | Desinicializa actual `EventTargetArray` clase.

### <a name="public-methods"></a>Métodos públicos

Name                                  | Descripción
------------------------------------- | ---------------------------------------------------------------------------------------
[EventTargetArray::AddTail](#addtail) | El controlador de eventos especificado se anexa al final de la matriz interna de controladores de eventos.
[EventTargetArray::Begin](#begin)     | Obtiene la dirección del primer elemento de la matriz interna de controladores de eventos.
[EventTargetArray::End](#end)         | Obtiene la dirección del último elemento de la matriz interna de controladores de eventos.
[EventTargetArray::Length](#length)   | Obtiene el número actual de elementos de la matriz interna de controladores de eventos.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`EventTargetArray`

## <a name="requirements"></a>Requisitos

**Encabezado:** event.h

**Espacio de nombres**: Microsoft::WRL::Details

## <a name="tilde-eventtargetarray"></a>EventTargetArray::~EventTargetArray

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
~EventTargetArray();
```

### <a name="remarks"></a>Comentarios

Desinicializa actual `EventTargetArray` clase.

## <a name="addtail"></a>EventTargetArray::AddTail

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
void AddTail(
   _In_ IUnknown* element
);
```

### <a name="parameters"></a>Parámetros

*element*<br/>
Puntero al controlador de eventos para anexar.

### <a name="remarks"></a>Comentarios

El controlador de eventos especificado se anexa al final de la matriz interna de controladores de eventos.

`AddTail()` está pensado para ser utilizado internamente por sólo el `EventSource` clase.

## <a name="begin"></a>EventTargetArray::Begin

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
ComPtr<IUnknown>* Begin();
```

### <a name="return-value"></a>Valor devuelto

La dirección del primer elemento de la matriz interna de controladores de eventos.

### <a name="remarks"></a>Comentarios

Obtiene la dirección del primer elemento de la matriz interna de controladores de eventos.

## <a name="end"></a>EventTargetArray::End

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
ComPtr<IUnknown>* End();
```

### <a name="return-value"></a>Valor devuelto

La dirección del último elemento de la matriz interna de controladores de eventos.

### <a name="remarks"></a>Comentarios

Obtiene la dirección del último elemento de la matriz interna de controladores de eventos.

## <a name="eventtargetarray"></a>EventTargetArray::EventTargetArray

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
EventTargetArray(
   _Out_ HRESULT* hr,
   size_t items
);
```

### <a name="parameters"></a>Parámetros

*hr*<br/>
Después de las operaciones de este constructor, parámetro *hr* indica si la asignación de la matriz se realizó correctamente o no. En la lista siguiente se muestra los valores posibles para *hr*.

+   S_OK<br/>
    La operación se realizó correctamente.

+   E_OUTOFMEMORY<br/>
    No se pudo asignar memoria para la matriz.

+   S_FALSE<br/>
    Parámetro *elementos* es menor o igual que cero.

*items*<br/>
El número de elementos de matriz que se va a asignar.

### <a name="remarks"></a>Comentarios

Inicializa una nueva instancia de la clase `EventTargetArray`.

`EventTargetArray` se usa para mantener una matriz de controladores de eventos en un `EventSource` objeto.

## <a name="length"></a>EventTargetArray::Length

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
size_t Length();
```

### <a name="return-value"></a>Valor devuelto

El número actual de elementos de la matriz interna de controladores de eventos.

### <a name="remarks"></a>Comentarios

Obtiene el número actual de elementos de la matriz interna de controladores de eventos.
