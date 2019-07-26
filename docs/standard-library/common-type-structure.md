---
title: common_type (Estructura)
ms.date: 11/04/2016
f1_keywords:
- chrono/std::common_type
ms.assetid: 2b42722c-c3dc-4d62-8613-0271e52b6f00
ms.openlocfilehash: 1f2a329894af88dfafc0616655bdf8c2ca91cf0a
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68453198"
---
# <a name="commontype-structure"></a>common_type (Estructura)

Describe especializaciones de la clase de plantilla [common_type](../standard-library/common-type-class.md) para las creaciones de instancias de [duration](../standard-library/duration-class.md) y [time_point](../standard-library/time-point-class.md).

## <a name="syntax"></a>Sintaxis

```cpp
template <class Rep1, class Period1,
    class Rep2, class Period2>
struct common_type
<chrono::duration<Rep1, Period1>,
chrono::duration<Rep2, Period2>>;

template <class Clock,
    class Duration1, class Duration2>
struct common_type
<chrono::time_point<Clock, Duration1>,
chrono::time_point<Clock, Duration2>>;
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<> crónico

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)\
[\<chrono>](../standard-library/chrono.md)
