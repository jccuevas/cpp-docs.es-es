---
title: Error irrecuperable C1510
ms.date: 04/11/2017
f1_keywords:
- C1510
helpviewer_keywords:
- C1510
ms.assetid: 150c827f-9514-41a9-8d7e-82f820749bcb
ms.openlocfilehash: f05f79ea78958a7d7a64f24bdce2d1151b93cdfb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50596240"
---
# <a name="fatal-error-c1510"></a>Error irrecuperable C1510

No se puede abrir el archivo clui.dll de recursos de idioma

El compilador no puede cargar la DLL de recursos de idioma.

Hay dos causas comunes de este problema. Cuando se usa el compilador de 32 bits y herramientas, verá este error para proyectos grandes que utilizan más de 2GB de memoria durante un vínculo. Una posible solución en los sistemas Windows de 64 bits es usar al nativo de 64 bits o entre el compilador y las herramientas para generar el código. Esto aprovecha el mayor espacio de memoria disponible para las aplicaciones de 64 bits. Si debe utilizar un compilador de 32 bits porque se está ejecutando en un sistema de 32 bits, en algunos casos puede aumentar la cantidad de memoria disponible para el vinculador a 3GB. Para obtener más información, consulte [Tuning de 4 gigabytes: BCDEdit y Boot.ini](https://msdn.microsoft.com/library/vs/alm/bb613473) y [BCDEdit /Set increaseuserva](https://msdn.microsoft.com/library/ff542202.aspx) comando.

La otra causa habitual es una instalación de Visual Studio interrumpida o está incompleta. En este caso, ejecute el instalador para reparar o reinstalar Visual Studio.
