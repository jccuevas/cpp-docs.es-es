---
title: Ejecución de programas de Linux en Windows
ms.date: 07/31/2019
helpviewer_keywords:
- Linux [C++], porting to Win32
ms.assetid: 3837e4fe-3f96-4f24-b2a1-7be94718a881
ms.openlocfilehash: c91bcf1c9384cd71811d42a14b98dc155626a4d5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368464"
---
# <a name="running-linux-programs-on-windows"></a>Ejecución de programas de Linux en Windows

Para ejecutar un programa de Linux en Windows, tiene estas opciones:

- Ejecute el programa tal cual en el subsistema de Windows para Linux (WSL). En WSL, el programa se ejecuta directamente en el hardware del equipo, no en una máquina virtual. WSL también habilita las llamadas directas del sistema de archivos entre sistemas Windows y Linux, lo que elimina la necesidad de transporte SSL. WSL está diseñado como un entorno de línea de comandos y no se recomienda para las aplicaciones que hagan un uso intensivo de los gráficos. Para obtener más información, consulte la [documentación del subsistema de Windows para Linux](/windows/wsl/about).
- Ejecute el programa tal cual en una máquina virtual de Linux o en un contenedor de Docker, ya sea en una máquina local o en Azure. Para obtener más información, consulte [Máquinas virtuales](https://azure.microsoft.com/services/virtual-machines/) y [Docker en Azure](https://docs.microsoft.com/azure/docker/).
- Compile el programa mediante gcc o clang en los entornos [MinGW](http://MinGW.org/) o [MinGW-w64](https://sourceforge.net/p/mingw-w64/wiki2/Home/), que proporcionan una capa de traducción de las llamadas del sistema de Linux al de Windows.
- Compile y ejecute el programa mediante gcc o clang en el entorno [Cygwin](https://www.cygwin.com/), que proporciona un entorno de Linux más completo en Windows en comparación con MinGW o MinGW-w64.
- Porte manualmente el código desde Linux y realice la compilación para Windows con Microsoft C++ (MSVC). Esto implica refactorizar código independiente de la plataforma en bibliotecas independientes y volver a escribir el código específico de Linux para usar código específico de Windows (por ejemplo, Win32 o API de DirectX). En el caso de las aplicaciones que requieren gráficos de alto rendimiento, esta es probablemente la mejor opción.
