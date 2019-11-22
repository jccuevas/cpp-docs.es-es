---
title: Macros de recursividad
description: Describe las macros que se usan para llamar a NMAKE en sesiones recursivas.
ms.date: 11/20/2019
helpviewer_keywords:
- NMAKE program, recursion macros
- recursion macros
- macros, recursion
ms.assetid: c53e5ae7-619e-46b1-bdc2-86d8c7798b1d
no-loc:
- MAKE
- MAKEDIR
- MAKEFLAGS
ms.openlocfilehash: f2bda23cb079e4fd7d12cea3598d33b3625c088d
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303149"
---
# <a name="recursion-macros"></a>Macros de recursividad

Utilice macros de recursividad para llamar a NMAKE de forma recursiva. Las sesiones recursivas heredan las macros de la línea de comandos y de la variable de entorno y la información de Tools. ini. No heredan las reglas de inferencia definidas por el archivo make ni las especificaciones de `.SUFFIXES` y `.PRECIOUS`. Hay tres maneras de pasar macros a una sesión NMAKE recursiva: establezca una variable de entorno con un comando :::no-loc text="SET"::: antes de la llamada recursiva. Defina una macro en el comando para la llamada recursiva. O bien, defina una macro en Tools. ini.

|Macro|Definición|
|-----------|----------------|
|**MAKE**|Comando que se usa originalmente para invocar NMAKE.<br /><br /> La macro `$(MAKE)` proporciona la ruta de acceso completa a NMAKE. exe.|
|**MAKEDIR**|Directorio actual cuando se invocó NMAKE.|
|**MAKEFLAGS**|Opciones actualmente en vigor. Use como `/$(MAKEFLAGS)`. La opción **/f** no está incluida.|

## <a name="see-also"></a>Vea también

[Macros NMAKE especiales](special-nmake-macros.md)
