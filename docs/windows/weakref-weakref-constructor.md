---
title: Constructor de Weakref | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::WeakRef::WeakRef
dev_langs:
- C++
helpviewer_keywords:
- WeakRef, constructor
ms.assetid: 589f87e0-8dcc-4e82-aab2-f2f66f1ec47c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d7c8bc81040ce8d4c1cea7497f9d1371fbb9d41f
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42611615"
---
# <a name="weakrefweakref-constructor"></a>WeakRef::WeakRef (Constructor)

Inicializa una nueva instancia de la **WeakRef** clase.

## <a name="syntax"></a>Sintaxis

```cpp
WeakRef();
WeakRef(
   decltype(__nullptr)  
);

WeakRef(
   _In_opt_ IWeakReference* ptr
);

WeakRef(
   const ComPtr<IWeakReference>& ptr
);

WeakRef(
   const WeakRef& ptr
);

WeakRef(
   _Inout_ WeakRef&& ptr
);
```

### <a name="parameters"></a>Parámetros

*ptr*  
Un puntero, referencia o referencia de valor r a un objeto existente que inicializa actual **WeakRef** objeto.

## <a name="remarks"></a>Comentarios

El primer constructor inicializa vacío **WeakRef** objeto. El segundo constructor inicializa un **WeakRef** objeto de un puntero a la `IWeakReference` interfaz. El tercer constructor inicializa un **WeakRef** objeto a partir de una referencia a un `ComPtr<IWeakReference>` objeto. Los constructores cuarto y quinto Inicializa un **WeakRef** objeto desde otro **WeakRef** objeto.

## <a name="requirements"></a>Requisitos

**Encabezado:** client.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también

[WeakRef (clase)](../windows/weakref-class.md)