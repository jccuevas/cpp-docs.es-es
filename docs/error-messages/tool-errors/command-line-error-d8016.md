---
title: Error de la línea de comandos D8016 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D8016
dev_langs:
- C++
helpviewer_keywords:
- D8016
ms.assetid: eec51312-7471-4f92-94b2-d517cafc8ef5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0ee16542b2f0cf9842e351813ed2e0b0d22cccaa
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46056994"
---
# <a name="command-line-error-d8016"></a>Error de la línea de comandos D8016

Opciones de línea de comandos 'opción1' y 'opción2' son incompatibles

Las opciones de línea de comandos no pueden especificarse juntos.

Compruebe las variables de entorno, como CL, especificaciones de opción.

**/ CLR** implica **/EHa**, y no se puede especificar cualquier otro **/EH** opción del compilador con **/CLR**. Para obtener más información, consulte [/clr (Compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).

D8016 puede aparecer después de actualizar un proyecto de Visual C++ 6.0: puede habilitar el proceso del Asistente para actualización de proyecto **/RTC** para cada archivo de código fuente en el proyecto, que reemplaza el **/RTC** establecer para el proyecto.  Para resolver, cambie el **/RTC** establecer para cada archivo de código fuente en el proyecto en la configuración predeterminada, lo que significa que la configuración del proyecto para **/RTC** entrará en vigor para cada archivo.

Consulte [/RTC (comprobaciones de errores de tiempo de ejecución)](../../build/reference/rtc-run-time-error-checks.md) para obtener información acerca de cómo cambiar la **/RTC** configuración de la propiedad.