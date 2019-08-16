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
ms.openlocfilehash: 004fe7ace6102feecbcb2f542b5b93268ae2f868
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493310"
---
# <a name="common-visual-c-64-bit-migration-issues"></a>Problemas comunes de migración a 64 bits en Visual C++

Cuando utilice el compilador de Microsoft C++ (MSVC) para crear aplicaciones que se ejecuten en un sistema operativo Windows de 64 bits, debe tener en cuenta los siguientes problemas:

- `int` y `long` son valores de 32 bits en sistemas operativos Windows de 64 bits. Debe tener cuidado de no asignar punteros a variables de 32 bits en los programas que piense compilar para plataformas de 64 bits. Los punteros son de 64 bits en las plataformas de 64 bits; si asigna un puntero a una variable de 32 bits, se truncará su valor.

- `size_t`, `time_t` y`ptrdiff_t` son valores de 64 bits en sistemas operativos Windows de 64 bits.

- `time_t`es un valor de 32 bits en sistemas operativos Windows de 32 bits en Visual Studio 2005 y versiones anteriores. `time_t` es ahora un entero de 64 bits de forma predeterminada. Para obtener más información, vea [Administración del tiempo](../c-runtime-library/time-management.md).

   Debe tener en cuenta los lugares en que el código toma un valor `int` y lo procesa como valor `size_t` o `time_t`. Es posible que el número aumente hasta superar un número de 32 bits y que los datos se trunquen al volver a pasarlo al almacenamiento `int`.

El modificador `printf` %x (`int` en formato hexadecimal) no funcionará según lo esperado en un sistema operativo Windows de 64 bits. Sólo operará en los primeros 32 bits del valor que se le pasa.

- Use % I32x para presentar un tipo entero de 32 bits en formato hexadecimal.

- Use % I32x para presentar un tipo entero de 64 bits en formato hexadecimal.

- El modificador %p (un puntero en formato hexadecimal) funcionará según lo esperado en un sistema operativo Windows de 64 bits.

Para más información, consulte:

- [Opciones del compilador de MSVC](reference/compiler-options.md)

- [Sugerencias para la migración](/windows/win32/WinProg64/migration-tips)

## <a name="see-also"></a>Vea también

[Configuración de proyectos de Visual C++ para destinos x64 de 64 bits](configuring-programs-for-64-bit-visual-cpp.md)<br/>
[Guía de migración y actualización de Visual C++](../porting/visual-cpp-porting-and-upgrading-guide.md)
