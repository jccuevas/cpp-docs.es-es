---
title: Getactivationfactory (método) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::GetActivationFactory
dev_langs:
- C++
helpviewer_keywords:
- GetActivationFactory method
ms.assetid: 59da8844-072e-414b-b89c-1db1cc4fd81d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0e87ea3b0e44732d4271385073c48fd92e1aa114
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42608932"
---
# <a name="modulegetactivationfactory-method"></a>Module::GetActivationFactory (Método)

Obtiene un generador de activación para el módulo.

## <a name="syntax"></a>Sintaxis

```cpp
WRL_NOTHROW HRESULT GetActivationFactory(
   _In_ HSTRING pActivatibleClassId,
   _Deref_out_ IActivationFactory **ppIFactory,
   wchar_t* serverName = nullptr
);
```

### <a name="parameters"></a>Parámetros

*pActivatibleClassId*  
IID de una clase en tiempo de ejecución.

*ppIFactory*  
IActivationFactory para la clase en tiempo de ejecución especificado.

*Nombre de servidor*  
El nombre de un subconjunto de los generadores de clases en el módulo actual. Especifique el nombre del servidor usado en el [ActivatableClassWithFactoryEx](../windows/activatableclass-macros.md) macro, o especificar **nullptr** para obtener el nombre del servidor predeterminado.

## <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; en caso contrario, el valor HRESULT devuelto por GetActivationFactory.

## <a name="requirements"></a>Requisitos

**Encabezado:** module.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también

[Module (clase)](../windows/module-class.md)  
[ActivatableClass (macros)](../windows/activatableclass-macros.md)