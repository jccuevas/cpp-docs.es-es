---
title: Registerwinrtobject (método) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::RegisterWinRTObject
dev_langs:
- C++
helpviewer_keywords:
- RegisterWinRTObject method
ms.assetid: a2782c9c-b9c5-4e4b-9c8d-ef513aea20c5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 496b1ccac5b998ba08f4e2eccfe31ffd18f2c37d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46431793"
---
# <a name="moduleregisterwinrtobject-method"></a>Module::RegisterWinRTObject (Método)

Registra uno o más objetos en tiempo de ejecución de Windows para que otras aplicaciones pueden conectarse a ellos.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT RegisterWinRTObject(const wchar_t* serverName,
   wchar_t** activatableClassIds,
   WINRT_REGISTRATION_COOKIE* cookie,
   unsigned int count)  
```

### <a name="parameters"></a>Parámetros

*Nombre de servidor*<br/>
Un nombre que especifica un subconjunto de los objetos afectados por esta operación.

*activatableClassIds*<br/>
Una matriz de CLSID activable para registrar.

*Cookie*<br/>
Un valor que identifica los objetos de clase que se registraron. Este valor se utiliza posteriormente para revocar el registro.

*count*<br/>
El número de objetos que se va a registrar.

## <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; en caso contrario, un error HRESULT como CO_E_OBJISREG que indica el motivo por el error en la operación.

## <a name="requirements"></a>Requisitos

**Encabezado:** module.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también

[Module (clase)](../windows/module-class.md)