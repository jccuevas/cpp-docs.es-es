---
title: Error grave de NMAKE U1045
ms.date: 08/11/2019
f1_keywords:
- U1045
helpviewer_keywords:
- U1045
ms.assetid: dc70d162-14b9-4107-9237-7514044d72e3
ms.openlocfilehash: bdc28bcf02aea791a346a0a74915707fef551b8b
ms.sourcegitcommit: db1ed91fa7451ade91c3fb76bc7a2b857f8a5eef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/13/2019
ms.locfileid: "68980546"
---
# <a name="nmake-fatal-error-u1045"></a>Error grave de NMAKE U1045

> error de generación: *mensaje*

No se pudo ejecutar un programa o un comando llamado por NMAKE por razón en el *mensaje*. Cuando NMAKE llama a otro programa, por ejemplo, el compilador o el vinculador, puede producirse un error en la llamada. O bien, el programa llamado puede devolver un error. Este mensaje se utiliza para informar sobre el error.

Para corregir este problema, primero hay que determinar la causa del error. Puede usar los comandos indicados por la opción NMAKE [/n](../../build/reference/running-nmake.md#nmake-options) para comprobar la configuración del entorno y repetir las acciones realizadas por NMAKE en la línea de comandos.
