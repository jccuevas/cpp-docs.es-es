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
ms.openlocfilehash: 705b495e3f6d626a742fd1a63989c8cc658446a4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46379674"
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

*ptr*<br/>
El nombre de un puntero a un tipo.

*riid*<br/>
El identificador de interfaz de `Base`.

*PPV*<br/>
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

[InterfaceTraits (estructura)](../windows/interfacetraits-structure.md)<br/>
[Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)