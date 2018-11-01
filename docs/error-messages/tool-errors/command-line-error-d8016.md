---
title: Error de la línea de comandos D8016
ms.date: 11/04/2016
f1_keywords:
- D8016
helpviewer_keywords:
- D8016
ms.assetid: eec51312-7471-4f92-94b2-d517cafc8ef5
ms.openlocfilehash: c1e2e3e28f8556416f58d68f8ef1df4b220bc54c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50567926"
---
# <a name="command-line-error-d8016"></a>Error de la línea de comandos D8016

Opciones de línea de comandos 'opción1' y 'opción2' son incompatibles

Las opciones de línea de comandos no pueden especificarse juntos.

Compruebe las variables de entorno, como CL, especificaciones de opción.

**/ CLR** implica **/EHa**, y no se puede especificar cualquier otro **/EH** opción del compilador con **/CLR**. Para obtener más información, consulte [/clr (Compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).

D8016 puede aparecer después de actualizar un proyecto de Visual C++ 6.0: puede habilitar el proceso del Asistente para actualización de proyecto **/RTC** para cada archivo de código fuente en el proyecto, que reemplaza el **/RTC** establecer para el proyecto.  Para resolver, cambie el **/RTC** establecer para cada archivo de código fuente en el proyecto en la configuración predeterminada, lo que significa que la configuración del proyecto para **/RTC** entrará en vigor para cada archivo.

Consulte [/RTC (comprobaciones de errores de tiempo de ejecución)](../../build/reference/rtc-run-time-error-checks.md) para obtener información acerca de cómo cambiar la **/RTC** configuración de la propiedad.