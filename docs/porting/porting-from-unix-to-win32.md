---
title: Ejecución de programas de Linux en Windows
ms.date: 07/31/2019
helpviewer_keywords:
- Linux [C++], porting to Win32
ms.assetid: 3837e4fe-3f96-4f24-b2a1-7be94718a881
ms.openlocfilehash: 6b59d7685aaada3ba44c03da2e5c27c75c8a473a
ms.sourcegitcommit: 725e86dabe2901175ecc63261c3bf05802dddff4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/31/2019
ms.locfileid: "68682384"
---
# <a name="running-linux-programs-on-windows"></a>Ejecución de programas de Linux en Windows

Para ejecutar un programa de Linux en Windows, tiene estas opciones:

- Ejecute el programa tal cual en el subsistema de Windows para Linux (WSL). En WSL, el programa se ejecuta directamente en el hardware del equipo, no en una máquina virtual. WSL también habilita las llamadas directas del sistema de archivos entre sistemas Windows y Linux, lo que elimina la necesidad de transporte SSL. WSL está diseñado como un entorno de línea de comandos y no se recomienda para las aplicaciones que hagan un uso intensivo de los gráficos. Para obtener más información, consulte la [documentación del subsistema de Windows para Linux](/windows/wsl/about).
- Ejecute el programa tal cual en una máquina virtual de Linux o en un contenedor de Docker, ya sea en una máquina local o en Azure. Para obtener más información, consulte [Máquinas virtuales](https://azure.microsoft.com/services/virtual-machines/) y [Docker en Azure](https://docs.microsoft.com/azure/docker/).
- Compile el programa mediante gcc o clang en los entornos [MinGW](http://MinGW.org/) o [MinGW-w64](https://MinGW-w64.org/doku.php), que proporcionan una capa de traducción de las llamadas del sistema de Linux al de Windows.
- Compile y ejecute el programa mediante gcc o clang en el entorno [Cygwin](https://www.cygwin.com/), que proporciona un entorno de Linux más completo en Windows en comparación con MinGW o MinGW-w64.
- Porte manualmente el código desde Linux y realice la compilación para Windows con Microsoft C++ (MSVC). Esto implica refactorizar código independiente de la plataforma en bibliotecas independientes y volver a escribir el código específico de Linux para usar código específico de Windows (por ejemplo, Win32 o API de DirectX). En el caso de las aplicaciones que requieren gráficos de alto rendimiento, esta es probablemente la mejor opción.

