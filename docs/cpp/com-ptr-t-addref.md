---
title: _com_ptr_t::AddRef
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::AddRef
helpviewer_keywords:
- AddRef method [C++], interface pointers
ms.assetid: c104dac3-aad3-40bb-a298-75c6cd0e63a2
ms.openlocfilehash: 7408b5c174f76673b56caffd56aaa87895bd08d4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154947"
---
# <a name="comptrtaddref"></a>_com_ptr_t::AddRef

**Específicos de Microsoft**

Las llamadas del `AddRef` función miembro de `IUnknown` en el puntero de interfaz encapsulado.

## <a name="syntax"></a>Sintaxis

```
void AddRef( );
```

## <a name="remarks"></a>Comentarios

Las llamadas `IUnknown::AddRef` en el puntero de interfaz encapsulado y generar un `E_POINTER` error si el puntero es NULL.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[_com_ptr_t (Clase)](../cpp/com-ptr-t-class.md)