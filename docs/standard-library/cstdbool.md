---
title: '&lt;cstdbool&gt;'
ms.date: 07/11/2019
f1_keywords:
- <cstdbool>
- cstdbool
helpviewer_keywords:
- cstdbool header
ms.assetid: 44ccb8b2-d808-4715-8097-58ba09ab33ed
ms.openlocfilehash: ed780e059a5e456731fd6a4f651639e282016f5e
ms.sourcegitcommit: 0867d648e0955ebad7260b5fbebfd6cd4d58f3c7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/19/2019
ms.locfileid: "68341101"
---
# <a name="ltcstdboolgt"></a>&lt;cstdbool&gt;

Incluye el encabezado \<stdbool. > h de la biblioteca estándar de C y agrega los nombres `std` asociados al espacio de nombres.

> [!NOTE]
> Dado que \<el encabezado stdbool. h > define macros que son palabras C++clave en, incluso no tiene ningún efecto. El \<encabezado stdbool. h > está en desuso en C++. El \<encabezado cstdbool > está en desuso en c++ 17 y se ha quitado en el borrador c++ 20 standard.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<> cstdbool

**Espacio de nombres:** std

## <a name="remarks"></a>Comentarios

Incluir este encabezado garantiza que los nombres declarados mediante vinculación externa en el encabezado de la biblioteca estándar `std` de C se declaran en el espacio de nombres.

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](cpp-standard-library-header-files.md)\
[C++Información general de la biblioteca estándar](cpp-standard-library-overview.md)\
[Seguridad para subprocesos en la C++ biblioteca estándar](thread-safety-in-the-cpp-standard-library.md)
