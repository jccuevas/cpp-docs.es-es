---
title: Macros de recursividad | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, recursion macros
- recursion macros
- macros, recursion
ms.assetid: c53e5ae7-619e-46b1-bdc2-86d8c7798b1d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f91a5f327686a522608b6eec9fd7106cbab00028
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45702045"
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