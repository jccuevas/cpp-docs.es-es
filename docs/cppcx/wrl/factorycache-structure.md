---
title: FactoryCache (estructura)
ms.date: 09/21/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::FactoryCache
- module/Microsoft::WRL::Details::FactoryCache::cookie
- module/Microsoft::WRL::Details::FactoryCache::factory
helpviewer_keywords:
- Microsoft::WRL::Details::FactoryCache structure
- Microsoft::WRL::Details::FactoryCache::cookie data member
- Microsoft::WRL::Details::FactoryCache::factory data member
ms.assetid: 624544e6-0989-47f6-a3e9-edb60e1ee6d4
ms.openlocfilehash: 507d35179b9fa86399e56b18171800f41eaf1f10
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371480"
---
# <a name="factorycache-structure"></a>FactoryCache (estructura)

Admite la infraestructura de la biblioteca de plantillas C++ de Windows runtime y no está diseñada para usarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
struct FactoryCache;
```

## <a name="remarks"></a>Observaciones

Contiene la ubicación de un generador de clases y un valor que identifica un wrt registrado o un objeto de clase COM.

## <a name="members"></a>Miembros

### <a name="public-data-members"></a>Miembros de datos públicos

Nombre                              | Descripción
--------------------------------- | ------------------------------------------------------------------------------------------------------------------------------
[FactoryCache::cookie](#cookie)   | Contiene un valor que identifica un objeto de clase COM o Windows Runtime registrado y, más adelante, se usa para anular el registro del objeto.
[FactoryCache::factory](#factory) | Apunta a un generador de clases com y en tiempo de ejecución de Windows.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`FactoryCache`

## <a name="requirements"></a>Requisitos

**Encabezado:** module.h

**Espacio de nombres:** Microsoft::WRL::Details

## <a name="factorycachecookie"></a><a name="cookie"></a>FactoryCache::cookie

Admite la infraestructura de la biblioteca de plantillas C++ de Windows runtime y no está diseñada para usarse directamente desde el código.

```cpp
union {
   WINRT_REGISTRATION_COOKIE winrt;
   DWORD com;
} cookie;
```

### <a name="remarks"></a>Observaciones

Contiene un valor que identifica un objeto de clase COM o Windows Runtime registrado y, más adelante, se usa para anular el registro del objeto.

## <a name="factorycachefactory"></a><a name="factory"></a>FactoryCache::factory

Admite la infraestructura de la biblioteca de plantillas C++ de Windows runtime y no está diseñada para usarse directamente desde el código.

```cpp
IUnknown* factory;
```

### <a name="remarks"></a>Observaciones

Apunta a un generador de clases com y en tiempo de ejecución de Windows.
