---
title: time_base (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- locale/std::time_base
dev_langs:
- C++
helpviewer_keywords:
- time_base class
ms.assetid: 9ae37f0b-9a42-496e-9870-3d9b71bab8fb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6e1111ede44edc36e5399d82b3c4e088b20cc1c9
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38957303"
---
# <a name="timebase-class"></a>time_base (Clase)

La clase que actúa como clase base para las facetas de la clase plantilla time_get y definir el tipo enumerado `dateorder` y varias constantes de este tipo.

## <a name="syntax"></a>Sintaxis

```cpp
class time_base : public locale::facet {
public:
    enum dateorder {no_order,
    dmy,
 mdy,
    ymd,
 ydm};
    time_base(
 size_t _Refs = 0)
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
