---
title: '&lt;ccomplex&gt;'
ms.date: 11/04/2016
f1_keywords:
- <ccomplex>
ms.assetid: a9fcb5f0-88e3-464b-a5fd-d1afb8cd7e6f
ms.openlocfilehash: ab9e95eb7b432a85a75d73d388ec069b0d04ac62
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/10/2018
ms.locfileid: "51517207"
---
# <a name="ltccomplexgt"></a>&lt;ccomplex&gt;

Incluye el encabezado [\<complex>](../standard-library/complex.md) de la biblioteca estándar de C++ que, de forma efectiva, incluye el encabezado \<complex.h> de la biblioteca estándar de C y agrega los nombres asociados al espacio de nombres `std`.

## <a name="syntax"></a>Sintaxis

```cpp
#include <ccomplex>
```

## <a name="remarks"></a>Comentarios

Incluir este encabezado también garantiza que los nombres declarados mediante vinculación externa en el encabezado de la biblioteca estándar de C se declaran en el espacio de nombres `std`.

El nombre `clog`, que está declarado en \<complex.h>, no está definido en el espacio de nombres `std` por los conflictos potenciales con el `clog` que está declarado en [\<iostream>](../standard-library/iostream.md).

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
[Información general sobre la biblioteca estándar de C++](../standard-library/cpp-standard-library-overview.md)<br/>
