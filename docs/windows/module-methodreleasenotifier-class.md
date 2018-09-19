---
title: Methodreleasenotifier (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::MethodReleaseNotifier
dev_langs:
- C++
helpviewer_keywords:
- MethodReleaseNotifier class
ms.assetid: 5c2902be-964b-488f-9f1c-adf504995cbc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cee634ab62e699b4de6af54a57b0fe3d6b5e9a40
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42606613"
---
# <a name="modulemethodreleasenotifier-class"></a>Module::MethodReleaseNotifier (Clase)

Invoca un controlador de eventos cuando se libera el último objeto del módulo actual. El controlador de eventos se especifica mediante un objeto y su miembro de puntero al método.

## <a name="syntax"></a>Sintaxis

```cpp
template<typename T>
class MethodReleaseNotifier : public ReleaseNotifier;
```

### <a name="parameters"></a>Parámetros

*T*  
El tipo del objeto cuya función miembro es el controlador de eventos.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[Module::MethodReleaseNotifier::MethodReleaseNotifier (constructor)](../windows/module-methodreleasenotifier-methodreleasenotifier-constructor.md)|Inicializa una nueva instancia de la **methodreleasenotifier** clase.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[Module::MethodReleaseNotifier::Invoke (método)](../windows/module-methodreleasenotifier-invoke-method.md)|Llama al controlador de eventos asociado con el actual **methodreleasenotifier** objeto.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|nombre|Descripción|
|----------|-----------------|
|[Module::MethodReleaseNotifier::method_ (miembro de datos)](../windows/module-methodreleasenotifier-method-data-member.md)|Contiene un puntero al controlador de eventos actual **methodreleasenotifier** objeto.|
|[Module::MethodReleaseNotifier::object_ (miembro de datos)](../windows/module-methodreleasenotifier-object-data-member.md)|Contiene un puntero al objeto cuya función miembro es el controlador de eventos actual **methodreleasenotifier** objeto.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`ReleaseNotifier`

`MethodReleaseNotifier`

## <a name="requirements"></a>Requisitos

**Encabezado:** module.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también
[Module (clase)](../windows/module-class.md)