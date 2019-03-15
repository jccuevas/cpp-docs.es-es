---
title: Macros de recursividad
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, recursion macros
- recursion macros
- macros, recursion
ms.assetid: c53e5ae7-619e-46b1-bdc2-86d8c7798b1d
ms.openlocfilehash: 064bc40906bcf3a126c225585a6df43443b5c38e
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57828025"
---
# <a name="recursion-macros"></a>Macros de recursividad

Usar macros de recursividad para llamar a NMAKE de forma recursiva. Las sesiones recursivas heredan macros de línea de comandos y variables de entorno y Tools.ini información. No heredan las reglas de inferencia definido por el archivo MAKE o **. SUFIJOS** y **. PRECIOSAS** especificaciones. Para pasar macros a una sesión NMAKE recursiva, establezca una variable de entorno con el conjunto antes de la llamada recursiva, defina una macro en el comando para la llamada recursiva o definir una macro en Tools.ini.

|Macro|de esquema JSON|
|-----------|----------------|
|**ASEGÚRESE DE**|Comando usado originalmente para llamar a NMAKE.<br /><br /> La macro $ (Make) proporciona la ruta de acceso completa a nmake.exe.|
|**MAKEDIR**|Directorio actual cuando se invocó NMAKE.|
|**MAKEFLAGS**|Opciones actualmente en vigor. Usar como `/$(MAKEFLAGS)`.  Tenga en cuenta que /F no se incluye.|

## <a name="see-also"></a>Vea también

[Macros NMAKE especiales](special-nmake-macros.md)
