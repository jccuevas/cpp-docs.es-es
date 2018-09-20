---
title: GetClassObject (método) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::GetClassObject
dev_langs:
- C++
helpviewer_keywords:
- GetClassObject method
ms.assetid: 95b0de1b-f728-4f96-9f44-f6ea71ce56e4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 90a1b527d12e581c42fc9519e56d453f845e0b63
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46419729"
---
# <a name="modulegetclassobject-method"></a>Module::GetClassObject (Método)

Recupera una memoria caché de generadores de clases.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetClassObject(
   REFCLSID clsid,
   REFIID riid,
   _Deref_out_ void **ppv,
   wchar_t* serverName = nullptr
);
```

### <a name="parameters"></a>Parámetros

*CLSID*<br/>
Identificador de clase.

*riid*<br/>
Id. de interfaz que solicita.

*PPV*<br/>
Puntero al objeto devuelto.

*Nombre de servidor*<br/>
El nombre del servidor que se especifica en uno el `ActivatableClassWithFactory`, `ActivatableClassWithFactoryEx`, o `ActivatableClass` macro; o **nullptr** para obtener el nombre del servidor predeterminado.

## <a name="return-value"></a>Valor devuelto

## <a name="remarks"></a>Comentarios

Use este método solo para COM, no el tiempo de ejecución de Windows. Este método solo expone `IClassFactory` métodos.

## <a name="requirements"></a>Requisitos

**Encabezado:** module.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también

[Module (clase)](../windows/module-class.md)