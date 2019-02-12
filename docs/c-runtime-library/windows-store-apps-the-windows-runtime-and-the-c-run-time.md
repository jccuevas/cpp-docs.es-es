---
title: Aplicaciones de la Plataforma universal de Windows, Windows Runtime y tiempo de ejecución de C
ms.date: 02/02/2019
ms.assetid: 356d6d8d-76ee-4181-9ad0-6f24b2fede38
ms.openlocfilehash: ae57390dc916116b8d799b9f937ff882abaef970
ms.sourcegitcommit: 63c072f5e941989636f5a2b13800b68bb7129931
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/06/2019
ms.locfileid: "55763900"
---
# <a name="uwp-apps-the-windows-runtime-and-the-c-run-time"></a>Aplicaciones de la Plataforma universal de Windows, Windows Runtime y tiempo de ejecución de C

Las aplicaciones de la Plataforma universal de Windows (UWP) son programas que se ejecutan en Windows Runtime, que se ejecuta en 8. Windows Runtime es un entorno de confianza que controla las funciones, las variables y los recursos que están disponibles para una aplicación de la Plataforma universal de Windows. Sin embargo, por su naturaleza, las restricciones de Windows Runtime impiden el uso de la mayoría de las características de la biblioteca en tiempo de ejecución de C (CRT) en las aplicaciones de la Plataforma universal de Windows.

Windows Runtime no admite las siguientes características de CRT:

- La mayoría de las funciones de CRT que están relacionadas con cierta funcionalidad no admitida.

   Por ejemplo, una aplicación de la Plataforma universal de Windows no puede crear un proceso mediante las familias de rutinas **exec** y **spawn**.

   Cuando una función de CRT no se admite en una aplicación de la Plataforma universal de Windows, este hecho se indica expresamente en su artículo de referencia.

- La mayoría de las funciones de cadena y carácter multibyte.

   Sin embargo, se admiten texto Unicode y ANSI.

- Variables de entorno.

- El concepto de un directorio de trabajo actual.

- Las aplicaciones y los archivos DLL de la Plataforma universal de Windows que están vinculados estáticamente a CRT y que se compilan con las opciones del compilador [/MT](../build/reference/md-mt-ld-use-run-time-library.md) o `/MTd`.

   Es decir, una aplicación que usa una versión estática multiproceso de CRT.

- Una aplicación que se compila mediante la opción del compilador [/MDd](../build/reference/md-mt-ld-use-run-time-library.md).

   Es decir, una versión de depuración multiproceso y específica para DLL de CRT. Este tipo de aplicación no se admiten en Windows Runtime.

Para obtener una lista completa de las funciones de CRT que no están disponibles en una aplicación de la Plataforma universal de Windows y sugerencias sobre funciones alternativas, vea [CRT functions not supported in Universal Windows Platform apps](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows).

## <a name="see-also"></a>Vea también

[Compatibilidad](../c-runtime-library/compatibility.md)<br/>
[Funciones de CRT no compatibles con Windows Runtime](../c-runtime-library/windows-runtime-unsupported-crt-functions.md)<br/>
[Rutinas en tiempo de ejecución Universal C por categoría](../c-runtime-library/run-time-routines-by-category.md)<br/>
[Creación de una aplicación de consola de la Plataforma universal de Windows](/windows/uwp/launch-resume/console-uwp)
