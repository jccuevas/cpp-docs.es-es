---
title: _com_ptr_t::Release | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_ptr_t.Release
- _com_ptr_t::Release
dev_langs:
- C++
helpviewer_keywords:
- Release method [C++]
ms.assetid: db448b34-0efa-4f02-b701-ad1ca3ae6ca5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 444f56c1a999f09a79d725173c9f0f19399ab363
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118367"
---
# <a name="comptrtrelease"></a>_com_ptr_t::Release

**Específicos de Microsoft**

Las llamadas del **versión** función miembro de `IUnknown` en el puntero de interfaz encapsulado.

## <a name="syntax"></a>Sintaxis

```
void Release( );
```

## <a name="remarks"></a>Comentarios

Las llamadas `IUnknown::Release` en el puntero de interfaz encapsulado y generar un `E_POINTER` error si este puntero de interfaz es NULL.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[_com_ptr_t (Clase)](../cpp/com-ptr-t-class.md)