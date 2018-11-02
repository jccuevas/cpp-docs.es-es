---
title: time_base (Clase)
ms.date: 11/04/2016
f1_keywords:
- locale/std::time_base
helpviewer_keywords:
- time_base class
ms.assetid: 9ae37f0b-9a42-496e-9870-3d9b71bab8fb
ms.openlocfilehash: e790237e506aa32bafdb39938d841307bbc4d9c3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50593406"
---
# <a name="timebase-class"></a>time_base (Clase)

La clase que actúa como clase base para las facetas de la clase plantilla time_get y definir el tipo enumerado `dateorder` y varias constantes de este tipo.

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

- `no_order` se especifica ningún orden determinado.

- `dmy` Especifica el orden día, mes, año, como en 2 de diciembre de 1979.

- `mdy` Especifica el orden mes, día, año, como se muestra en el 2 de diciembre de 1979.

- `ymd` Especifica el orden año, mes, día, como en 1979/12/2.

- `ydm` Especifica el orden año, día, mes, como en 1979:2 Dic.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<locale>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
