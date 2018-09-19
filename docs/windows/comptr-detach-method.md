---
title: Método Comptr | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::Detach
dev_langs:
- C++
helpviewer_keywords:
- Detach method
ms.assetid: b9016775-1ade-4581-be1f-0d6f9c2ca658
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 84db0a82dfe6f9333f6a533aa9bc2bb529854fa2
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42593417"
---
# <a name="comptrdetach-method"></a>ComPtr::Detach (Método)

Desasocia esta **ComPtr** objeto desde la interfaz que representa.

## <a name="syntax"></a>Sintaxis

```cpp
T* Detach();
```

## <a name="return-value"></a>Valor devuelto

Un puntero a la interfaz que se ha representado por este **ComPtr** objeto.

## <a name="requirements"></a>Requisitos

**Encabezado:** client.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también

[ComPtr (clase)](../windows/comptr-class.md)