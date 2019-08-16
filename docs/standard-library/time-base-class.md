---
title: time_base (Clase)
ms.date: 11/04/2016
f1_keywords:
- locale/std::time_base
helpviewer_keywords:
- time_base class
ms.assetid: 9ae37f0b-9a42-496e-9870-3d9b71bab8fb
ms.openlocfilehash: 85565dc0c0ec904551eb8dd981cfacc9a2e1f256
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460036"
---
# <a name="timebase-class"></a>time_base (Clase)

La clase actúa como una clase base para las caras de la clase de plantilla time_get, que define solo el `dateorder` tipo enumerado y varias constantes de este tipo.

## <a name="syntax"></a>Sintaxis

```cpp
class time_base : public locale::facet {
public:
    enum dateorder {
        no_order,
        dmy,
        mdy,
        ymd,
        ydm
    };
    time_base(size_t _Refs = 0)
    ~time_base();
};
```

## <a name="remarks"></a>Comentarios

Cada constante caracteriza otra forma de ordenar los componentes de una fecha. Las constantes son:

- `no_order`no especifica ningún orden concreto.

- `dmy`especifica el orden del día, el mes y el año, como en el 2 de diciembre de 1979.

- `mdy`especifica el orden mes, día y año, como en el 2 de diciembre de 1979.

- `ymd`especifica el orden año, mes y día, como en 1979/12/2.

- `ydm`especifica el orden año, día y mes, como en 1979: 2 Dec

## <a name="requirements"></a>Requisitos

**Encabezado:** \<locale>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
