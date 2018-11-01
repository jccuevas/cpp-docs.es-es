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
ms.openlocfilehash: 7196363567dffa43844bbbd1de76934a317302d1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50545852"
---
# <a name="factorycache-structure"></a>FactoryCache (estructura)

Admite la infraestructura de la biblioteca de plantillas C++ de Windows en tiempo de ejecución y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
struct FactoryCache;
```

## <a name="remarks"></a>Comentarios

Contiene la ubicación de un generador de clases y un valor que identifica un registrados wrt o el objeto COM de la clase.

## <a name="members"></a>Miembros

### <a name="public-data-members"></a>Miembros de datos públicos

Name                              | Descripción
--------------------------------- | ------------------------------------------------------------------------------------------------------------------------------
[Factorycache](#cookie)   | Contiene un valor que identifica un objeto de clase en tiempo de ejecución de Windows o COM registrado y se utiliza posteriormente para anular el registro del objeto.
[Factorycache](#factory) | Apunta a un generador de clases COM o en tiempo de ejecución de Windows.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`FactoryCache`

## <a name="requirements"></a>Requisitos

**Encabezado:** module.h

**Namespace:** wrl

## <a name="cookie"></a>Factorycache

Admite la infraestructura de la biblioteca de plantillas C++ de Windows en tiempo de ejecución y no está pensado para utilizarse directamente desde el código.

```cpp
union {
   WINRT_REGISTRATION_COOKIE winrt;
   DWORD com;
} cookie;
```

### <a name="remarks"></a>Comentarios

Contiene un valor que identifica un objeto de clase en tiempo de ejecución de Windows o COM registrado y se utiliza posteriormente para anular el registro del objeto.

## <a name="factory"></a>Factorycache

Admite la infraestructura de la biblioteca de plantillas C++ de Windows en tiempo de ejecución y no está pensado para utilizarse directamente desde el código.

```cpp
IUnknown* factory;
```

### <a name="remarks"></a>Comentarios

Apunta a un generador de clases COM o en tiempo de ejecución de Windows.
