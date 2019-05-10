---
title: Problemas comunes de migración a 64 bits en Visual C++
ms.date: 05/06/2019
helpviewer_keywords:
- 64-bit programming [C++], migration
- 64-bit compiler [C++], migration
- porting 32-bit code to 64-bit code
- migration [C++], 64-bit code issues
- 32-bit code porting [C++]
- 64-bit applications [C++]
- 64-bit compiler [C++], porting 32-bit code
- Win64 [C++]
ms.assetid: d17fb838-7513-4e2d-8b27-a1666f17ad76
ms.openlocfilehash: b03ccc76163d79688a98ec89df241292e3eef112
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220875"
---
# <a name="common-visual-c-64-bit-migration-issues"></a>Problemas comunes de migración a 64 bits en Visual C++

Cuando se usa Microsoft C++ compilador (MSVC) para crear las aplicaciones se ejecuten en un sistema operativo de Windows de 64 bits, debe tener en cuenta lo siguiente:

- `int` y `long` son valores de 32 bits en sistemas operativos Windows de 64 bits. Debe tener cuidado de no asignar punteros a variables de 32 bits en los programas que piense compilar para plataformas de 64 bits. Los punteros son de 64 bits en las plataformas de 64 bits; si asigna un puntero a una variable de 32 bits, se truncará su valor.

- `size_t`, `time_t`, y `ptrdiff_t` son valores de 64 bits en sistemas operativos de Windows de 64 bits.

- `time_t` es un valor de 32 bits en sistemas de operativos Windows de 32 bits en Visual Studio 2005 y versiones anteriores. `time_t` es ahora un entero de 64 bits de forma predeterminada. Para obtener más información, consulte [administración del tiempo](../c-runtime-library/time-management.md).

   Debe tener en cuenta los lugares en que el código toma un valor `int` y lo procesa como valor `size_t` o `time_t`. Es posible que el número aumente hasta superar un número de 32 bits y que los datos se trunquen al volver a pasarlo al almacenamiento `int`.

El modificador `printf` %x (`int` en formato hexadecimal) no funcionará según lo esperado en un sistema operativo Windows de 64 bits. Sólo operará en los primeros 32 bits del valor que se le pasa.

- Use % I32x para presentar un tipo entero de 32 bits en formato hexadecimal.

- Use % I32x para presentar un tipo entero de 64 bits en formato hexadecimal.

- El modificador %p (un puntero en formato hexadecimal) funcionará según lo esperado en un sistema operativo Windows de 64 bits.

Para obtener más información, consulte:

- [Opciones del compilador de MSVC](reference/compiler-options.md)

- [Sugerencias de migración](/windows/desktop/WinProg64/migration-tips)

## <a name="see-also"></a>Vea también

[Configurar los proyectos de C++ de 64 bits, x64 destinos](configuring-programs-for-64-bit-visual-cpp.md)<br/>
[Guía de migración y actualización de Visual C++](../porting/visual-cpp-porting-and-upgrading-guide.md)
