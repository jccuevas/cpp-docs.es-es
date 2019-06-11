---
title: Compatibilidad
ms.date: 11/04/2016
f1_keywords:
- c.programs
helpviewer_keywords:
- CRT, compatibility
- compatibility, C run-time libraries
- compatibility
ms.assetid: 346709cb-edda-4909-9a19-3d253eddb6b7
ms.openlocfilehash: 5e9d2edca8da128343bd14ea86a8c1c0023a244b
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2019
ms.locfileid: "65446669"
---
# <a name="compatibility"></a>Compatibilidad

La biblioteca en tiempo de ejecución de C Universal (UCRT) admite la mayor parte de la biblioteca estándar de C requerida para la conformidad con C++. Implementa la biblioteca C99 (ISO/IEC 9899:1999), con las excepciones de las macros de tipo genérico definidas en \<tgmath.h> y la compatibilidad de tipos estricta en \<complex.h>. La UCRT también implementa un gran subconjunto de la biblioteca de C POSIX.1 (ISO/IEC 9945-1:1996, la interfaz de programación de aplicaciones de sistema de POSIX), pero no cumple totalmente ningún estándar POSIX concreto.  Además, la UCRT implementa varias macros y funciones específicas de Microsoft que no forman parte de un estándar.

Las funciones concretas de la implementación de Microsoft de Visual C++ se encuentran en la biblioteca vcruntime.  Muchas de estas funciones son para uso interno y no es posible llamarlas mediante código de usuario. Algunas están documentadas para su uso en la depuración y la compatibilidad de implementación.

El estándar de C++ reserva los nombres que comienzan con un carácter de subrayado en el espacio de nombres global para la implementación. Como las funciones POSIX están en el espacio de nombres global, pero no forman parte de la biblioteca en tiempo de ejecución estándar de C, las implementaciones específicas de Microsoft de estas funciones tienen un carácter de subrayado inicial. Para la portabilidad, la UCRT también admite los nombres predeterminados, pero el compilador de Microsoft C++ emite una advertencia de desuso cuando se compila código que los usa. Solo los nombres POSIX predeterminados están en desuso, las funciones no. Para suprimir la advertencia, defina `_CRT_NONSTDC_NO_WARNINGS` antes de incluir encabezados en el código que utiliza los nombres POSIX originales.

Algunas funciones de la biblioteca de C estándar tienen un historial de uso no seguro, debido a mal uso de parámetros y búferes sin comprobar. Estas funciones son a menudo el origen de los problemas de seguridad en el código. Microsoft creó un conjunto de versiones más seguras de estas funciones que comprueban el uso de parámetros e invocan el controlador de parámetros no válidos si se detecta un problema en tiempo de ejecución.  De forma predeterminada, el compilador de Microsoft C++ emite una advertencia de desuso cuando se utiliza una función que tiene una variante más segura disponible. Al compilar el código como C++, puede definir `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` en 1 para eliminar la mayoría de las advertencias. De esta forma, se usan sobrecargas de plantilla para llamar a las variantes más seguras a la vez que se mantiene el código portable. Para suprimir la advertencia, defina `_CRT_SECURE_NO_WARNINGS` antes de incluir encabezados en el código que utiliza estas funciones. Para obtener más información, consulta [Security Features in the CRT](../c-runtime-library/security-features-in-the-crt.md).

A menos que se indique lo contrario en la documentación de funciones concretas, la UCRT es compatible con la API de Windows.  Algunas funciones no se admiten en aplicaciones de la Tienda de Windows 8 ni en aplicaciones de la Plataforma universal de Windows en Windows 10. Estas funciones se muestran en el artículo [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md), en el que se enumeran las funciones no admitidas por Windows Runtime ni la [UWP](/uwp).

## <a name="related-articles"></a>Artículos relacionados

|Title|Descripción|
|-----------|-----------------|
|[Aplicaciones de UWP, Windows Runtime y runtime de C](../c-runtime-library/windows-store-apps-the-windows-runtime-and-the-c-run-time.md)|Describe cuándo no son compatibles las rutinas UCRT con aplicaciones universales de Windows o de Microsoft Store.|
|[Conformidad con ANSI C](../c-runtime-library/ansi-c-compliance.md)|Describe la nomenclatura conforme a los estándares en la UCRT.|
|[UNIX](../c-runtime-library/unix.md)|Proporciona directrices para trasladar programas a UNIX.|
|[Plataformas de Windows (CRT)](../c-runtime-library/windows-platforms-crt.md)|Enumera los sistemas operativos que admite CRT.|
|[Compatibilidad con versiones anteriores](../c-runtime-library/backward-compatibility.md)|Describe cómo asignar nombres de CRT antiguos a los nombres nuevos.|
|[Características de la biblioteca CRT](../c-runtime-library/crt-library-features.md)|Proporciona información general sobre los archivos de biblioteca (.lib) de CRT y las opciones del compilador asociadas.|