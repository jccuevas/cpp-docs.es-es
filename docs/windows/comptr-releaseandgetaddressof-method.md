---
title: Releaseandgetaddressof (método) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::ReleaseAndGetAddressOf
dev_langs:
- C++
helpviewer_keywords:
- ReleaseAndGetAddressOf method
ms.assetid: 3751dcb4-d50e-432c-89e4-e736be34d434
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7f4aee13808fd55c42319aab90c13af7922ed9d2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46394847"
---
# <a name="comptrreleaseandgetaddressof-method"></a>ComPtr::ReleaseAndGetAddressOf (Método)

Libera la interfaz asociada a este **ComPtr** y, a continuación, recupera la dirección de la [ptr_](../windows/comptr-ptr-data-member.md) miembro de datos que contiene un puntero a la interfaz que se publicó.

## <a name="syntax"></a>Sintaxis

```cpp
T** ReleaseAndGetAddressOf();
```

## <a name="return-value"></a>Valor devuelto

La dirección de la [ptr_](../windows/comptr-ptr-data-member.md) miembro de datos de este **ComPtr**.

## <a name="requirements"></a>Requisitos

**Encabezado:** client.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también

[ComPtr (clase)](../windows/comptr-class.md)<br/>
[ComPtr::ptr_ (miembro de datos)](../windows/comptr-ptr-data-member.md)