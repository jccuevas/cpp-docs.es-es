---
title: alignment_of (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- type_traits/std::alignment_of
dev_langs:
- C++
helpviewer_keywords:
- alignment_of class
- alignment_of
ms.assetid: 4141c59a-f94e-41c4-93fd-9ea578b27387
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9af19f046cf6de44448e3fcddf97584f58adc9ae
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="alignmentof-class"></a>alignment_of (Clase)

Obtiene una alineación del tipo especificado. Este struct se implementa en términos de [alignof](../cpp/alignof-and-alignas-cpp.md). Use `alignof` directamente cuando solo sea necesario consultar un valor de alineación. Use alignment_of cuando necesite una constante integral, por ejemplo, al realizar un envío de etiquetas.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Ty>
struct alignment_of;
```

### <a name="parameters"></a>Parámetros

`Ty` El tipo de consulta.

## <a name="remarks"></a>Comentarios

La consulta de tipo contiene el valor de la alineación del tipo `Ty`.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
[aligned_storage (Clase)](../standard-library/aligned-storage-class.md)<br/>
