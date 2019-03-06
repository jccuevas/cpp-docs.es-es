---
title: Macros de recursividad
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, recursion macros
- recursion macros
- macros, recursion
ms.assetid: c53e5ae7-619e-46b1-bdc2-86d8c7798b1d
ms.openlocfilehash: c04b23d4c8116fdf898c2f732b63c5e02adf5661
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57416415"
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
