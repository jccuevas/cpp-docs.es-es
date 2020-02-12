---
title: progress_reporter (clase)
ms.date: 11/04/2016
f1_keywords:
- progress_reporter
- PPLTASKS/concurrency::progress_reporter
- PPLTASKS/concurrency::progress_reporter::progress_reporter
- PPLTASKS/concurrency::progress_reporter::report
helpviewer_keywords:
- progress_reporter class
ms.assetid: b836efab-2d05-4649-b6fa-d15236f1f813
ms.openlocfilehash: bd8f50a8c9829ff9de3e2412b89aa4de88d90db6
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77138770"
---
# <a name="progress_reporter-class"></a>progress_reporter (clase)

La clase del informador de progreso que permite informar de notificaciones de progreso de un tipo específico. Cada objeto progress_reporter se vincula a una acción u operación asincrónica determinada.

## <a name="syntax"></a>Sintaxis

```cpp
template<typename _ProgressType>
class progress_reporter;
```

### <a name="parameters"></a>Parámetros

*_ProgressType*<br/>
El tipo de carga de cada notificación de progreso que se notifican a través del informador de progreso.

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[progress_reporter](#ctor)||

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[enviar](#report)|Envía un informe de progreso a la operación o acción asincrónica a la que está enlazado este informador de progreso.|

## <a name="remarks"></a>Observaciones

Este tipo solo está disponible para Windows Runtime aplicaciones.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`progress_reporter`

## <a name="requirements"></a>Requisitos

**Encabezado:** ppltasks. h

**Espacio de nombres:** simultaneidad

## <a name="ctor"></a>progress_reporter

```cpp
progress_reporter();
```

## <a name="report"></a>enviar

Envía un informe de progreso a la operación o acción asincrónica a la que está enlazado este informador de progreso.

```cpp
void report(const _ProgressType& val) const;
```

### <a name="parameters"></a>Parámetros

*val*<br/>
Carga que se va a notificar a través de una notificación de progreso.

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)
