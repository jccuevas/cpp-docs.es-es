---
title: FactoryCache (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 09/21/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::FactoryCache
- module/Microsoft::WRL::Details::FactoryCache::cookie
- module/Microsoft::WRL::Details::FactoryCache::factory
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Details::FactoryCache structure
- Microsoft::WRL::Details::FactoryCache::cookie data member
- Microsoft::WRL::Details::FactoryCache::factory data member
ms.assetid: 624544e6-0989-47f6-a3e9-edb60e1ee6d4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d56779b5df33f75c9147d34b55f8c2fc65204a82
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/03/2018
ms.locfileid: "48234546"
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
