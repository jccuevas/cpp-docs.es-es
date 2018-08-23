---
title: Método hstring | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::Set
dev_langs:
- C++
ms.assetid: c9b3d613-95c4-48b0-999d-f5baf0804faf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6eb2261ab973245c78ec8f5e0269663e5181a0ab
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42590046"
---
# <a name="hstringset-method"></a>HString::Set (Método)

Establece el valor del elemento actual **HString** objeto en la cadena especificada de caracteres anchos o **HString** parámetro.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT Set(
          const wchar_t* str) throw();
HRESULT Set(
          const wchar_t* str,
          unsigned int len
           ) throw();
HRESULT Set(
          const HSTRING& hstr
           ) throw();
```

### <a name="parameters"></a>Parámetros

*str*  
Una cadena de caracteres anchos.

*Len*  
La longitud máxima de la *str* parámetro que se asigna a la actual **HString** objeto.

*HSTR*  
Existente **HString** objeto.

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Namespace:** Wrappers

## <a name="see-also"></a>Vea también

[HString (clase)](../windows/hstring-class.md)