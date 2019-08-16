---
title: Error irrecuperable C1510
ms.date: 04/11/2017
f1_keywords:
- C1510
helpviewer_keywords:
- C1510
ms.assetid: 150c827f-9514-41a9-8d7e-82f820749bcb
ms.openlocfilehash: 33c17a3099f4aed99cc26579d0e65c4a350b4268
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501091"
---
# <a name="fatal-error-c1510"></a>Error irrecuperable C1510

No se puede abrir el archivo clui.dll de recursos de idioma

El compilador no puede cargar el archivo DLL de recursos de idioma.

Hay dos causas comunes para este problema. Al usar el compilador y las herramientas de 32 bits, puede ver este error en proyectos grandes que usan más de 2 GB de memoria durante un vínculo. Una posible solución en los sistemas de Windows de 64 bits es usar el compilador y las herramientas nativas y cruzadas de 64 bits para generar el código. Esto aprovecha el mayor espacio de memoria disponible para las aplicaciones de 64 bits. Si debe usar un compilador de 32 bits porque está ejecutando en un sistema de 32 bits, en algunos casos puede aumentar la cantidad de memoria disponible para el enlazador a 3 GB. Para obtener más información, [consulte Optimización de 4 gigabytes: Bcdedit y boot. ini](/windows/win32/memory/4-gigabyte-tuning) y el comando [bcdedit/Set increaseuserva](/windows-hardware/drivers/devtest/bcdedit--set) .

La otra causa común es una instalación de Visual Studio interrumpida o incompleta. En este caso, vuelva a ejecutar el instalador para reparar o reinstalar Visual Studio.
