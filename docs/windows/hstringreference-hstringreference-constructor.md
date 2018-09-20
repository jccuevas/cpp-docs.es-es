---
title: Constructor Hstringreference | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::HStringReference
dev_langs:
- C++
ms.assetid: 29f5fe11-3928-4f60-9861-f0894247bfcb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6123f87abb9922a9736ac56f64d28e78887a0fdd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46403590"
---
# <a name="hstringreferencehstringreference-constructor"></a>HStringReference::HStringReference (Constructor)

Inicializa una nueva instancia de la **HStringReference** clase.

## <a name="syntax"></a>Sintaxis

```cpp
template<unsigned int sizeDest>
HStringReference(wchar_t const (&str)[ sizeDest]) throw();

template<unsigned int sizeDest>
HStringReference(wchar_t const (&str)[ sizeDest],
                 unsigned int len) throw();

HStringReference(HStringReference&& other) throw();
```

### <a name="parameters"></a>Parámetros

*sizeDest*<br/>
Un parámetro de plantilla que especifica el tamaño del destino **HStringReference** búfer.

*str*<br/>
Una referencia a una cadena de caracteres anchos.

*Len*<br/>
La longitud máxima de la *str* búfer de parámetro para utilizar en esta operación. Si el *len* parámetro no se especifica, toda la *str* se usa el parámetro. Si *len* es mayor que *sizeDest*, *len* está establecido en *sizeDest*-1.

*other*<br/>
Otro **HStringReference** objeto.

## <a name="remarks"></a>Comentarios

El primer constructor inicializa un nuevo **HStringReference** objeto que el mismo tamaño que el parámetro *str*.

El segundo constructor inicializa una nueva **HStringReference** objeto al que el specifeid tamaño por parámetro *len*.

El tercer constructor inicializa una nueva **HStringReference** objeto por el valor de la *otros* parámetro y, a continuación, se destruye el *otros* parámetro.

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Namespace:** Wrappers

## <a name="see-also"></a>Vea también

[HStringReference (clase)](../windows/hstringreference-class.md)