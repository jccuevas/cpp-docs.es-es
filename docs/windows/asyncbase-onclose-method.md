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
ms.openlocfilehash: fd6bd03b1e5aa3f690d93a5c51cc6664e0547c2e
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42597354"
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

[AsyncBase (clase)](../windows/asyncbase-class.md)  
[AsyncBase::Close (método)](../windows/asyncbase-close-method.md)