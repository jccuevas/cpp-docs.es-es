---
title: Rendimiento de bibliotecas multiproceso | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- threading [C++], performance
- libraries, multithreaded
- performance, multithreading
- multithreaded libraries
ms.assetid: faa5d808-087c-463d-8f0d-8c478d137296
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9f66aebc7b6d77e3697fabf783332a83bdd6f3fb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46052112"
---
# <a name="multithreaded-libraries-performance"></a>Rendimiento de bibliotecas multiproceso

El CRT de un solo subproceso ya no está disponible. En este tema se describe cómo obtener el máximo rendimiento de las bibliotecas multiproceso.

## <a name="maximizing-performance"></a>Maximizar el rendimiento

El rendimiento de las bibliotecas multiproceso se ha mejorado y ha llegado casi al nivel de rendimiento de las bibliotecas de un único subproceso ya eliminadas. Para aquellas situaciones en que se precisa de un rendimiento incluso mayor, hay varias características nuevas.

- El bloqueo de secuencia independiente permite bloquear una secuencia y, después, usar [_nolock (funciones)](../c-runtime-library/nolock-functions.md) para acceder directamente a la secuencia. Esto permite que el uso del bloqueo se active fuera de bucles críticos.

- La configuración regional por subproceso reduce el costo de acceso de configuración regional para escenarios multiproceso (vea [_configthreadlocale](../c-runtime-library/reference/configthreadlocale.md)).

- Las funciones dependientes de la configuración regional (cuyos nombres terminan en _l) toman la configuración regional como parámetro, lo que permite evitar un costo considerable (por ejemplo, [printf, _printf_l, wprintf, _wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)).

- Las optimizaciones para las páginas de códigos comunes reducen el costo de muchas operaciones cortas.

- Definir [_CRT_DISABLE_PERFCRIT_LOCKS](../c-runtime-library/crt-disable-perfcrit-locks.md) obliga a todas las operaciones de E/S a asumir un modelo de E/S de un único subproceso y utilizar los formularios de _nolock de las funciones. Esto aumenta el rendimiento de las aplicaciones de un único subproceso con un uso elevado de E/S.

- La exposición del identificador de montón de CRT permite habilitar el mecanismo de montón de fragmentación baja (LFH) de Windows para el montón de CRT, lo que puede mejorar considerablemente el rendimiento en escenarios de alta escalabilidad.

## <a name="see-also"></a>Vea también

[Características de la biblioteca CRT](../c-runtime-library/crt-library-features.md)