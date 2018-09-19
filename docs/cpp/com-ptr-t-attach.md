---
title: _com_ptr_t::Attach | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::Attach
dev_langs:
- C++
helpviewer_keywords:
- COM interfaces, attach pointer
- Attach method [C++]
ms.assetid: 94c18e0a-06be-4ca7-bdaf-cd54ec0a645e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f2fbedb2bbfba16abf1196d1dba377f7589c916b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099621"
---
# <a name="comptrtattach"></a>_com_ptr_t::Attach

**Específicos de Microsoft**

Encapsula un puntero de interfaz sin formato del tipo de este puntero inteligente.

## <a name="syntax"></a>Sintaxis

```
void Attach( Interface* pInterface ) throw( );
void Attach( Interface* pInterface, bool fAddRef ) throw( );
```

#### <a name="parameters"></a>Parámetros

*pInterface*<br/>
Puntero a interfaz sin formato.

*fAddRef*<br/>
Si es TRUE, a continuación, `AddRef` se llama. Si es FALSE, el `_com_ptr_t` objeto toma la propiedad del puntero de interfaz sin formato sin llamar a `AddRef`.

## <a name="remarks"></a>Comentarios

- **Adjuntar (***pInterface***)** `AddRef` no se llama. La propiedad de la interfaz se pasa a este objeto `_com_ptr_t`. `Release` se llama para disminuir el recuento de referencias para el puntero previamente encapsulado.

- **Adjuntar (***pInterface* **,***fAddRef***)** si *fAddRef* es TRUE, `AddRef`se llama para incrementar el recuento de referencias para el puntero de interfaz encapsulado. Si *fAddRef* es FALSE, esto `_com_ptr_t` objeto toma la propiedad del puntero de interfaz sin formato sin llamar a `AddRef`. `Release` se llama para disminuir el recuento de referencias para el puntero previamente encapsulado.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[_com_ptr_t (Clase)](../cpp/com-ptr-t-class.md)