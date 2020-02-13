---
title: accelerator_view_removed (Clase)
ms.date: 03/27/2019
f1_keywords:
- accelerator_view_removed
- AMPRT/accelerator_view_removed
- AMPRT/Concurrency::accelerator_view_removed::accelerator_view_removed
- AMPRT/Concurrency::accelerator_view_removed::get_view_removed_reason
helpviewer_keywords:
- AMPRT/Concurrency::accelerator_view_removed::accelerator_view_removed Class
ms.assetid: 262446de-311c-454e-a5ed-e2aaced0d88a
ms.openlocfilehash: 9a3f6f349fc3103893639fe209dcf23a07ffec56
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127129"
---
# <a name="accelerator_view_removed-class"></a>accelerator_view_removed (Clase)

Excepción que se produce cuando se produce un error en una llamada de DirectX subyacente debido al mecanismo de detección y recuperación de tiempo de espera de Windows.

## <a name="syntax"></a>Sintaxis

```cpp
class accelerator_view_removed : public runtime_exception;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[Constructor de accelerator_view_removed](#ctor)|Inicializa una nueva instancia de la clase `accelerator_view_removed`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[get_view_removed_reason](#get_view_removed_reason)|Devuelve un código de error HRESULT que indica la causa de la eliminación del objeto `accelerator_view`.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`exception`

`runtime_exception`

`out_of_memory`

## <a name="requirements"></a>Requisitos

**Encabezado:** amprt. h

**Espacio de nombres:** Concurrency

## <a name="ctor"></a>accelerator_view_removed

Inicializa una nueva instancia de la clase [accelerator_view_removed](accelerator-view-removed-class.md) .

### <a name="syntax"></a>Sintaxis

```cpp
explicit accelerator_view_removed(
    const char * message,
    HRESULT view_removed_reason ) throw();

explicit accelerator_view_removed(
    HRESULT view_removed_reason ) throw();
```

### <a name="parameters"></a>Parámetros

*message*<br/>
Descripción del error.

*view_removed_reason*<br/>
Un código de error HRESULT que indica la causa de la eliminación del objeto `accelerator_view`.

### <a name="return-value"></a>Valor devuelto

Nueva instancia de la clase `accelerator_view_removed`.

## <a name="get_view_removed_reason"></a>get_view_removed_reason

Devuelve un código de error HRESULT que indica la causa de la eliminación del objeto `accelerator_view`.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT get_view_removed_reason() const throw();
```

## <a name="see-also"></a>Consulte también

[Espacio de nombres de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)
