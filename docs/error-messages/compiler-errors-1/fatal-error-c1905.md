---
title: Error irrecuperable C1905
ms.date: 11/04/2016
f1_keywords:
- C1905
helpviewer_keywords:
- C1905
ms.assetid: fefc6769-477f-45a2-9878-6f0a5f42472c
ms.openlocfilehash: 106dfe8a078047225097686d185a1ba43987ce33
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202636"
---
# <a name="fatal-error-c1905"></a>Error irrecuperable C1905

Front-end y back-end no compatibles (el destino debe ser el mismo procesador).

Este error se produce cuando un front-end del compilador (C1. dll) genera un archivo. obj que tiene como destino un procesador, como x86, ARM o x64, pero lo lee un back-end (C2. dll) que tiene como destino un procesador diferente.

Para resolver este problema, asegúrese de que el front-end y el back-end utilizados se corresponden. Este es el valor predeterminado para los proyectos creados en Visual Studio. Este error puede producirse si ha editado el archivo de proyecto y si ha utilizado diferentes rutas de acceso a las herramientas del compilador. Si no ha establecido específicamente la ruta de acceso de las herramientas del compilador, este error puede producirse si la instalación de Visual Studio está dañada. Por ejemplo, tal vez ha copiado los archivos .dll del compilador de una ubicación a otra. Use **programas y características** en el panel de control de Windows para reparar o reinstalar Visual Studio.
