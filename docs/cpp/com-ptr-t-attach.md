---
title: _com_ptr_t::Attach
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::Attach
helpviewer_keywords:
- COM interfaces, attach pointer
- Attach method [C++]
ms.assetid: 94c18e0a-06be-4ca7-bdaf-cd54ec0a645e
ms.openlocfilehash: 057d784bb495aefaeec1b86697a7421f6464cbd7
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81745071"
---
# <a name="_com_ptr_tattach"></a>_com_ptr_t::Attach

**Microsoft Specific**

Encapsula un puntero de interfaz sin formato del tipo de este puntero inteligente.

## <a name="syntax"></a>Sintaxis

```cpp
void Attach( Interface* pInterface ) throw( );
void Attach( Interface* pInterface, bool fAddRef ) throw( );
```

#### <a name="parameters"></a>Parámetros

*pInterface*<br/>
Puntero a interfaz sin formato.

*fAddRef*<br/>
Si es TRUE, `AddRef` se llama. Si es FALSE, `_com_ptr_t` el objeto toma la propiedad `AddRef`del puntero de interfaz sin formato sin llamar a .

## <a name="remarks"></a>Observaciones

- No se llama a **Attach(***pInterface***).** `AddRef`     La propiedad de la interfaz se pasa a este objeto `_com_ptr_t`. `Release`se llama para disminuir el recuento de referencias para el puntero encapsulado anteriormente.

- **Attach(**  *pInterface* **,**  *fAddRef*  **)** Si *fAddRef* es `AddRef` TRUE, se llama para incrementar el recuento de referencias para el puntero de interfaz encapsulado. Si *fAddRef* es `_com_ptr_t` FALSE, este objeto toma la `AddRef`propiedad del puntero de interfaz sin formato sin llamar a . `Release`se llama para disminuir el recuento de referencias para el puntero encapsulado anteriormente.

**END Microsoft Specific**

## <a name="see-also"></a>Vea también

[Clase _com_ptr_t](../cpp/com-ptr-t-class.md)
