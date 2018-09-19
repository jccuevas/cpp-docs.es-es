---
title: _com_ptr_t::Detach | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::Detach
dev_langs:
- C++
helpviewer_keywords:
- Detach method [C++]
ms.assetid: 0652053e-af37-44e9-a278-2522212ebfed
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a7f2f44df96ca339e5d8e4b251b5f2d259cb606b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46092146"
---
# <a name="comptrtdetach"></a>_com_ptr_t::Detach

**Específicos de Microsoft**

Extrae y devuelve el puntero de interfaz encapsulado.

## <a name="syntax"></a>Sintaxis

```
Interface* Detach( ) throw( );
```

## <a name="remarks"></a>Comentarios

Extrae y devuelve el puntero de interfaz encapsulado y, a continuación, borra el almacenamiento del puntero encapsulado en NULL. Esto quita el puntero de interfaz de la encapsulación. Es decisión suya llamar a `Release` en el puntero de interfaz devuelto.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[_com_ptr_t (Clase)](../cpp/com-ptr-t-class.md)