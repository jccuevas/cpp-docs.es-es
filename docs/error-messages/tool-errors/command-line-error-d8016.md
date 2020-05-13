---
title: Error de la línea de comandos D8016
ms.date: 11/04/2016
f1_keywords:
- D8016
helpviewer_keywords:
- D8016
ms.assetid: eec51312-7471-4f92-94b2-d517cafc8ef5
ms.openlocfilehash: 1bdef16b14488be86aff880db7c049f4bcddcdb5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196968"
---
# <a name="command-line-error-d8016"></a>Error de la línea de comandos D8016

las opciones de línea de comandos ' Opción1 ' y ' opción2 ' son incompatibles

Las opciones de línea de comandos no se pueden especificar juntas.

Compruebe las variables de entorno, como CL, para conocer las especificaciones de las opciones.

**/CLR** implica **/EHA**, y no se puede especificar ninguna otra opción del compilador **/EH** con **/CLR**. Para obtener más información, consulta [/clr (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md).

Puede obtener D8016 después de actualizar un proyecto C++ de Visual 6,0: el proceso del Asistente para actualización de proyectos puede habilitar **/RTC** en cada archivo de código fuente del proyecto, lo que invalida el valor **/RTC** para el proyecto.  Para resolverlo, cambie el valor de **/RTC** de cada archivo de código fuente del proyecto a la configuración predeterminada, lo que significa que la configuración del proyecto para **/RTC** estará en vigor para cada archivo.

Vea [/RTC (comprobaciones de errores en tiempo de ejecución)](../../build/reference/rtc-run-time-error-checks.md) para obtener información sobre cómo cambiar el valor de la propiedad **/RTC** .
