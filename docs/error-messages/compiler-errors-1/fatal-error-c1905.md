---
title: Error irrecuperable C1905
ms.date: 11/04/2016
f1_keywords:
- C1905
helpviewer_keywords:
- C1905
ms.assetid: fefc6769-477f-45a2-9878-6f0a5f42472c
ms.openlocfilehash: 3fb4db30d91e0dd8c9dbeeebca46210122e5ff07
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62166820"
---
# <a name="fatal-error-c1905"></a>Error irrecuperable C1905

Front-end y back-end no compatibles (el destino debe ser el mismo procesador).

Este error se produce cuando un archivo .obj es generado por un front-end del compilador (C1.dll) cuyo destino es un procesador, como x86, ARM o x64, pero se está leyendo un back-end (C2.dll) destinado a un procesador diferente.

Para resolver este problema, asegúrese de que el front-end y el back-end utilizados se corresponden. Este es el valor predeterminado para los proyectos creados en Visual Studio. Este error puede producirse si ha editado el archivo de proyecto y si ha utilizado diferentes rutas de acceso a las herramientas del compilador. Si no ha establecido específicamente la ruta de acceso de las herramientas del compilador, este error puede producirse si la instalación de Visual Studio está dañada. Por ejemplo, tal vez ha copiado los archivos .dll del compilador de una ubicación a otra. Use **programas y características** en el Panel de Control de Windows para reparar o reinstalar Visual Studio.