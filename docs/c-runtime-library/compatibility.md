---
title: Compatibilidad
description: Describe la compatibilidad de la biblioteca en tiempo de ejecución de C de Microsoft universal (UCRT) con la biblioteca estándar de C, POSIX, CRT seguro y aplicaciones de la tienda.
ms.date: 12/06/2019
helpviewer_keywords:
- CRT, compatibility
- compatibility, C run-time libraries
- compatibility
ms.assetid: 346709cb-edda-4909-9a19-3d253eddb6b7
ms.openlocfilehash: 39b936acc43243973c2f66ef6fc7306026cc3259
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171052"
---
# <a name="compatibility"></a>Compatibilidad

La biblioteca en tiempo de ejecución de C Universal (UCRT) admite la mayor parte de la biblioteca estándar de C requerida para la conformidad con C++. Implementa la biblioteca C99 (ISO/IEC 9899:1999), con ciertas excepciones: las macros de tipo genérico definidas en \<tgmath. h > y la compatibilidad de tipos estricta en \<> Complex. h. El UCRT también implementa un gran subconjunto de la biblioteca C de POSIX. 1 (ISO/IEC 9945-1:1996, la interfaz de programación de aplicaciones del sistema POSIX). Sin embargo, no es totalmente compatible con ningún estándar POSIX específico. UCRT también implementa varias macros y funciones específicas de Microsoft que no forman parte de un estándar.

Las funciones concretas de la implementación de Microsoft de Visual C++ se encuentran en la biblioteca vcruntime.  Muchas de estas funciones son para uso interno y el código de usuario no puede llamarlas. Algunas están documentadas para su uso en la depuración y la compatibilidad de implementación.

El estándar de C++ reserva los nombres que comienzan con un carácter de subrayado en el espacio de nombres global para la implementación. Las funciones POSIX y las funciones de la biblioteca en tiempo de ejecución específicas de Microsoft están en el espacio de nombres global, pero no forman parte de la biblioteca estándar en tiempo de ejecución de C. Este es el motivo por el que las implementaciones preferidas de Microsoft de estas funciones tienen un carácter de subrayado inicial. Para la portabilidad, la UCRT también admite los nombres predeterminados, pero el compilador de Microsoft C++ emite una advertencia de desuso cuando se compila código que los usa. Solo los nombres predeterminados están en desuso, no las propias funciones. Para suprimir la advertencia, defina `_CRT_NONSTDC_NO_WARNINGS` antes de incluir encabezados en el código que utiliza los nombres POSIX originales.

Algunas funciones de la biblioteca de C estándar tienen un historial de uso no seguro, debido a mal uso de parámetros y búferes sin comprobar. Estas funciones son a menudo el origen de los problemas de seguridad en el código. Microsoft creó un conjunto de versiones más seguras de estas funciones que comprueban el uso de los parámetros. Invocan el controlador de parámetros no válidos cuando se detecta un problema en tiempo de ejecución.  De forma predeterminada, el compilador de Microsoft C++ emite una advertencia de desuso cuando se utiliza una función que tiene una variante más segura disponible. Al compilar el código C++como, puede definir `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` como 1 para eliminar la mayoría de las advertencias. Esta macro permite que las sobrecargas de plantilla llamen a las variantes más seguras a la vez que mantienen el código fuente portátil. Para suprimir la advertencia, defina `_CRT_SECURE_NO_WARNINGS` antes de incluir encabezados en el código que utiliza estas funciones. Para obtener más información, consulte [Características de seguridad de CRT](../c-runtime-library/security-features-in-the-crt.md).

A menos que se indique lo contrario en la documentación de funciones concretas, la UCRT es compatible con la API de Windows.  Ciertas funciones no se admiten en aplicaciones de la tienda Windows o Plataforma universal de Windows ([UWP](/uwp)). Estas funciones se muestran en [funciones de CRT no admitidas en plataforma universal de Windows aplicaciones](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="related-articles"></a>Artículos relacionados

|Título|Descripción|
|-----------|-----------------|
|[Aplicaciones de UWP, Windows Runtime y runtime de C](../c-runtime-library/windows-store-apps-the-windows-runtime-and-the-c-run-time.md)|Describe cuándo las rutinas de UCRT no son compatibles con aplicaciones universales de Windows o aplicaciones Microsoft Store.|
|[Conformidad con ANSI C](../c-runtime-library/ansi-c-compliance.md)|Describe la nomenclatura conforme a los estándares en la UCRT.|
|[UNIX](../c-runtime-library/unix.md)|Proporciona directrices para trasladar programas a UNIX.|
|[Plataformas de Windows (CRT)](../c-runtime-library/windows-platforms-crt.md)|Enumera los sistemas operativos que admite CRT.|
|[Compatibilidad con versiones anteriores](../c-runtime-library/backward-compatibility.md)|Describe cómo asignar nombres de CRT antiguos a los nombres nuevos.|
|[Características de la biblioteca CRT](../c-runtime-library/crt-library-features.md)|Proporciona información general sobre los archivos de biblioteca (.lib) de CRT y las opciones del compilador asociadas.|
