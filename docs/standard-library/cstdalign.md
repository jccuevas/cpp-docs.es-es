---
title: '&lt;cstdalign&gt;'
ms.date: 07/11/2019
f1_keywords:
- <cstdalign>
- cstdalign
- __alignas_is_defined
- __alignof_is_defined
helpviewer_keywords:
- cstdalign header
- __alignas_is_defined
- __alignof_is_defined
ms.assetid: 9d570924-d299-4225-9a58-8c4c820f5903
ms.openlocfilehash: 603a590190c50495aa80f1b41a574149eb8f760a
ms.sourcegitcommit: 0867d648e0955ebad7260b5fbebfd6cd4d58f3c7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/19/2019
ms.locfileid: "68342844"
---
# <a name="ltcstdaligngt"></a>&lt;cstdalign&gt;

En algunas C++ implementaciones de biblioteca estándar, este encabezado incluye el encabezado \<stdalign. > h de la biblioteca estándar de C y agrega los nombres `std` asociados al espacio de nombres. Dado que ese encabezado no está implementado en \<MSVC, el encabezado de > cstdalign `__alignas_is_defined` define `__alignof_is_defined`las macros de compatibilidad y.

> [!NOTE]
> Dado que \<el encabezado stdalign. h > define macros que son palabras C++clave en, incluso no tiene ningún efecto. El \<encabezado stdalign. h > está en desuso en C++. El \<encabezado cstdalign > está en desuso en c++ 17 y se ha quitado en el borrador c++ 20 standard.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<> cstdalign

**Espacio de nombres:** std

## <a name="macros"></a>Macros

| Macro | DESCRIPCIÓN |
| - | - |
| `__alignas_is_defined` | Una macro de compatibilidad de C que se expande a la constante de entero 1. |
| `__alignof_is_defined` | Una macro de compatibilidad de C que se expande a la constante de entero 1. |

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](cpp-standard-library-header-files.md)\
[C++Información general de la biblioteca estándar](cpp-standard-library-overview.md)\
[Seguridad para subprocesos en la C++ biblioteca estándar](thread-safety-in-the-cpp-standard-library.md)
