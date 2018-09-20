---
title: Constructor de hstring | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::HString
dev_langs:
- C++
ms.assetid: 6da12785-ed01-4720-a004-667db60298f1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 59ec7c1635b825cc300e28e5c02e2a3864a6c123
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46442258"
---
# <a name="hstringhstring-constructor"></a>HString::HString (Constructor)

Inicializa una nueva instancia de la **HString** clase.

## <a name="syntax"></a>Sintaxis

```cpp
HString(HSTRING hstr = nullptr) throw();
HString(HString&& other) throw();
```

#### <a name="parameters"></a>Parámetros

*HSTR*<br/>
Un identificador HSTRING.

*other*<br/>
Existente **HString** objeto.

## <a name="remarks"></a>Comentarios

El primer constructor inicializa un nuevo **HString** objeto que está vacía.

El segundo constructor inicializa una nueva **HString** objeto por el valor de la existente *otros* parámetro y, a continuación, se destruye el *otros* parámetro.

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Namespace:** Wrappers

## <a name="see-also"></a>Vea también

[HString (clase)](../windows/hstring-class.md)