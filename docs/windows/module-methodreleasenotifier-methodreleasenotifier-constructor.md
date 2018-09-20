---
title: Methodreleasenotifier (Constructor) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::MethodReleaseNotifier::MethodReleaseNotifier
dev_langs:
- C++
helpviewer_keywords:
- MethodReleaseNotifier, constructor
ms.assetid: 762e2ca4-0a92-49de-9ff5-d3efa0f067c0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 608a885eb446860cca43e5fabd19597d7611e633
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46386827"
---
# <a name="modulemethodreleasenotifiermethodreleasenotifier-constructor"></a>Module::MethodReleaseNotifier::MethodReleaseNotifier (Constructor)

Inicializa una nueva instancia de la **methodreleasenotifier** clase.

## <a name="syntax"></a>Sintaxis

```cpp
MethodReleaseNotifier(
   _In_ T* object,
   _In_ void (T::* method)(),
   bool release) throw() :
            ReleaseNotifier(release), object_(object),
            method_(method);
```

### <a name="parameters"></a>Parámetros

*object*<br/>
Objeto cuya función miembro es un controlador de eventos.

*Método*<br/>
La función miembro de parámetro *objeto* que es el controlador de eventos.

*release*<br/>
Especificar **true** para habilitar una llamada subyacente [módulo:: ReleaseNotifier::Release()](../windows/module-releasenotifier-release.md) método; en caso contrario, especifique **false**.

## <a name="requirements"></a>Requisitos

**Encabezado:** module.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también

[Module::MethodReleaseNotifier (clase)](../windows/module-methodreleasenotifier-class.md)