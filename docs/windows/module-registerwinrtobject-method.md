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
ms.openlocfilehash: a7f5879a3a76e9af795a5dfc808423b43515662a
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42609306"
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

*Nombre de servidor*  
Un nombre que especifica un subconjunto de los objetos afectados por esta operación.

*activatableClassIds*  
Una matriz de CLSID activable para registrar.

*Cookie*  
Un valor que identifica los objetos de clase que se registraron. Este valor se utiliza posteriormente para revocar el registro.

*count*  
El número de objetos que se va a registrar.

## <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; en caso contrario, un error HRESULT como CO_E_OBJISREG que indica el motivo por el error en la operación.

## <a name="requirements"></a>Requisitos

**Encabezado:** module.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también
[Module (clase)](../windows/module-class.md)