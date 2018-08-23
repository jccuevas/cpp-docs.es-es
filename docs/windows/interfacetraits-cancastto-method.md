---
title: Método Interfacetraits | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceTraits::CanCastTo
dev_langs:
- C++
helpviewer_keywords:
- CanCastTo method
ms.assetid: 275847cb-69ea-42bf-910f-05ba6ef8b48d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: aea326149c9748ff480d523a1078f54ba733cb14
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42610425"
---
# <a name="interfacetraitscancastto-method"></a>InterfaceTraits::CanCastTo (Método)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
template<typename T>
static __forceinline bool CanCastTo(
   _In_ T* ptr,
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>Parámetros

*ptr*  
El nombre de un puntero a un tipo.

*riid*  
El identificador de interfaz de `Base`.

*PPV*  
Si esta operación se realiza correctamente, *ppv* apunta a la interfaz especificada por `Base`. En caso contrario, *ppv* está establecido en **nullptr**.

## <a name="return-value"></a>Valor devuelto

**True** si esta operación se realiza correctamente y *ptr* se convierte en un puntero a `Base`; en caso contrario, **false** .

## <a name="remarks"></a>Comentarios

Indica si el puntero especificado se puede convertir en un puntero a `Base`.

Para obtener más información acerca de `Base`, consulte el **Typedefs pública** sección [InterfaceTraits (estructura)](../windows/interfacetraits-structure.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Namespace:** wrl

## <a name="see-also"></a>Vea también

[InterfaceTraits (estructura)](../windows/interfacetraits-structure.md)  
[Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)