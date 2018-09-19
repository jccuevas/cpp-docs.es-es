---
title: 'WeakReference:: Resolve (método) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::WeakReference::Resolve
dev_langs:
- C++
helpviewer_keywords:
- Resolve method
ms.assetid: fc65a4b7-48a0-4d64-a793-37f566fdd8e7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 59e748ef68d78f9cb77eb335f5c5cd44e058f0d4
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42601161"
---
# <a name="weakreferenceresolve-method"></a>WeakReference::Resolve (Método)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(Resolve)  
   (REFIID riid,
   _Deref_out_opt_ IInspectable **ppvObject
);
```

### <a name="parameters"></a>Parámetros

*riid*  
Id. de interfaz.

*ppvObject*  
Cuando se completa esta operación, una copia de la referencia segura actual si el recuento de referencia segura es distinto de cero.

## <a name="return-value"></a>Valor devuelto

- S_OK si esta operación se realiza correctamente y el recuento de referencia segura es cero. El *ppvObject* parámetro está establecido en **nullptr**.

- S_OK si esta operación se realiza correctamente y el recuento de referencia segura es distinto de cero. El *ppvObject* parámetro está establecido en la referencia segura.

- En caso contrario, un HRESULT que indica el motivo por el error de la operación.

## <a name="remarks"></a>Comentarios

Establece el puntero especificado en el valor de referencia segura actual si el recuento de referencia segura es distinto de cero.

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Namespace:** wrl

## <a name="see-also"></a>Vea también

[WeakReference (Class1)](../windows/weakreference-class1.md)  
[Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)