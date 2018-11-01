---
title: Macros de recursividad
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, recursion macros
- recursion macros
- macros, recursion
ms.assetid: c53e5ae7-619e-46b1-bdc2-86d8c7798b1d
ms.openlocfilehash: 0005a4be0422ed83816eabc7b55932a81441ae25
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50451264"
---
# <a name="recursion-macros"></a>Macros de recursividad

Usar macros de recursividad para llamar a NMAKE de forma recursiva. Las sesiones recursivas heredan macros de línea de comandos y variables de entorno y Tools.ini información. No heredan las reglas de inferencia definido por el archivo MAKE o **. SUFIJOS** y **. PRECIOSAS** especificaciones. Para pasar macros a una sesión NMAKE recursiva, establezca una variable de entorno con el conjunto antes de la llamada recursiva, defina una macro en el comando para la llamada recursiva o definir una macro en Tools.ini.

|Macro|de esquema JSON|
|-----------|----------------|
|**ASEGÚRESE DE**|Comando usado originalmente para llamar a NMAKE.<br /><br /> La macro $ (Make) proporciona la ruta de acceso completa a nmake.exe.|
|**MAKEDIR**|Directorio actual cuando se invocó NMAKE.|
|**MAKEFLAGS**|Opciones actualmente en vigor. Usar como `/$(MAKEFLAGS)`.  Tenga en cuenta que /F no se incluye.|

## <a name="see-also"></a>Vea también

[Macros NMAKE especiales](../build/special-nmake-macros.md)