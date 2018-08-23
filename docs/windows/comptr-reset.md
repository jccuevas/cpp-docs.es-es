---
title: ComPtr::Reset | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: aa6a46f7-f56b-4fd5-add0-7cea55f7abda
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 86e7716ff4e9a0b4f5132abfd431a2649f22f80f
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42593098"
---
# <a name="comptrreset"></a>ComPtr::Reset

Libera todas las referencias del puntero a la interfaz que está asociado a este **ComPtr**.

## <a name="syntax"></a>Sintaxis

```cpp
unsigned long Reset();
```

## <a name="return-value"></a>Valor devuelto

El número de referencias liberado, si existe.

## <a name="requirements"></a>Requisitos

**Encabezado:** client.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también

[ComPtr (clase)](../windows/comptr-class.md)