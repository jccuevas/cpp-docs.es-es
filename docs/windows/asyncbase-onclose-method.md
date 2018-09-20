---
title: Método Asyncbase | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::OnClose
dev_langs:
- C++
helpviewer_keywords:
- OnClose method
ms.assetid: 96766450-c262-4611-8534-7d190b799142
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 866e4a285a92fb7d80d0fe0d8240ebdda107de23
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46419404"
---
# <a name="asyncbaseonclose-method"></a>AsyncBase::OnClose (Método)

Cuando se invalida en una clase derivada, cierra una operación asincrónica.

## <a name="syntax"></a>Sintaxis

```cpp
virtual void OnClose(
   void
) = 0;
```

## <a name="requirements"></a>Requisitos

**Encabezado:** async.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también

[AsyncBase (clase)](../windows/asyncbase-class.md)<br/>
[AsyncBase::Close (método)](../windows/asyncbase-close-method.md)