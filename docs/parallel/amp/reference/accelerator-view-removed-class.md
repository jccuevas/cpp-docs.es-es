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
ms.openlocfilehash: 09f534a90f3191025c3ce99d07a462908387c676
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405656"
---
# <a name="acceleratorviewremoved-class"></a>accelerator_view_removed (Clase)

La excepción que se produce cuando una llamada de DirectX subyacente produce un error porque el mecanismo de detección y recuperación de tiempo de espera de Windows.

## <a name="syntax"></a>Sintaxis

```
class accelerator_view_removed : public runtime_exception;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[accelerator_view_removed (Constructor)](#ctor)|Inicializa una nueva instancia de la clase `accelerator_view_removed`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[get_view_removed_reason](#get_view_removed_reason)|Devuelve un código de error HRESULT que indica la causa de la `accelerator_view` eliminación del objeto.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`exception`

`runtime_exception`

`out_of_memory`

## <a name="requirements"></a>Requisitos

**Encabezado:** amprt.h

**Espacio de nombres**: simultaneidad

## <a name="ctor"></a> accelerator_view_removed)

Inicializa una nueva instancia de la [accelerator_view_removed ()](accelerator-view-removed-class.md) clase.

### <a name="syntax"></a>Sintaxis

```
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
Un código de error HRESULT que indica la causa de la eliminación de la `accelerator_view` objeto.

### <a name="return-value"></a>Valor devuelto

Nueva instancia de la clase `accelerator_view_removed`.

## <a name="getviewremovedreason"></a>get_view_removed_reason

Devuelve un código de error HRESULT que indica la causa de la `accelerator_view` eliminación del objeto.

### <a name="syntax"></a>Sintaxis

```
HRESULT get_view_removed_reason() const throw();
```

## <a name="see-also"></a>Vea también

[Espacio de nombres de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)
