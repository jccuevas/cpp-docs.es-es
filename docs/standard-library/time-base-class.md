---
title: time_base (Clase)
ms.date: 11/04/2016
f1_keywords:
- locale/std::time_base
helpviewer_keywords:
- time_base class
ms.assetid: 9ae37f0b-9a42-496e-9870-3d9b71bab8fb
ms.openlocfilehash: ddaf9905e859c062031940d35adfa2a3393dbb5a
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/21/2019
ms.locfileid: "72685789"
---
# <a name="time_base-class"></a>time_base (Clase)

La clase actúa como una clase base para las caras de la plantilla de clase time_get, que define simplemente el tipo enumerado `dateorder` y varias constantes de este tipo.

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

- `no_order` no especifica ningún orden concreto.

- `dmy` especifica el orden del día, el mes y el año, como en el 2 de diciembre de 1979.

- `mdy` especifica el orden mes, día y año, como en el 2 de diciembre de 1979.

- `ymd` especifica el orden año, mes y día, como en 1979/12/2.

- `ydm` especifica el orden año, día y mes, como en 1979:2 Dic.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<locale>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
