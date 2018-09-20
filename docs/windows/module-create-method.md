---
title: Método Module | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::Create
dev_langs:
- C++
helpviewer_keywords:
- Create method
ms.assetid: bfa97fd7-5226-4604-92a5-3b9697053e64
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a8b84bcaec7dbadfb7b735264df12f7e958dcd20
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46444702"
---
# <a name="modulecreate-method"></a>Module::Create (Método)

Crea una instancia de un módulo.

## <a name="syntax"></a>Sintaxis

```cpp
WRL_NOTHROW static Module& Create();
template<typename T>
WRL_NOTHROW static Module& Create(
   T callback
);
template<typename T>
WRL_NOTHROW static Module& Create(
   _In_ T* object,
   _In_ void (T::* method)()  
);
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Tipo de módulo.

*devolución de llamada*<br/>
Se llama cuando se libera el último objeto de instancia del módulo.

*object*<br/>
El *objeto* y *método* parámetros se utilizan en combinación. Señala al último objeto de instancia cuando se libera el último objeto de instancia en el módulo.

*Método*<br/>
El *objeto* y *método* parámetros se utilizan en combinación. Señala al método del último objeto de instancia cuando se libera el último objeto de instancia en el módulo.

## <a name="return-value"></a>Valor devuelto

Referencia al módulo.

## <a name="requirements"></a>Requisitos

**Encabezado:** module.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también

[Module (clase)](../windows/module-class.md)