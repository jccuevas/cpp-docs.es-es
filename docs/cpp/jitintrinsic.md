---
title: jitintrinsic
ms.date: 11/04/2016
f1_keywords:
- jitintrinsic
- jitintrinsic_cpp
helpviewer_keywords:
- __declspec keyword [C++], jitintrinsic
- jitintrinsic __declspec modifier
ms.assetid: 23dbe416-7ef6-442b-b16d-9a81aab04fa6
ms.openlocfilehash: 4626ba82d1d24582951bbffd8e6be687007d390f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178201"
---
# <a name="jitintrinsic"></a>jitintrinsic

Marca la función como significativa para Common Language Runtime de 64 bits. Se utiliza en algunas funciones de bibliotecas proporcionadas por Microsoft.

## <a name="syntax"></a>Sintaxis

```
__declspec(jitintrinsic)
```

## <a name="remarks"></a>Observaciones

**jitintrinsic** agrega un MODOPT (<xref:System.Runtime.CompilerServices.IsJitIntrinsic>) a una firma de función.

No se recomienda a los usuarios usar este modificador **__declspec** , ya que pueden producirse resultados inesperados.

## <a name="see-also"></a>Consulte también

[__declspec](../cpp/declspec.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)
