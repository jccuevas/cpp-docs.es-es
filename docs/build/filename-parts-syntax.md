---
title: Sintaxis de partes del nombre de archivo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- syntax, filename-parts
- filename-parts syntax in NMAKE
- NMAKE program, syntax
ms.assetid: 48fe38e0-3f3b-40e6-894c-330ee775a656
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d807087be171a2ad63ed37a8b359c3200c812040
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="filename-parts-syntax"></a>Sintaxis de las partes de un nombre de archivo
Sintaxis de partes del nombre de archivo en los comandos representa componentes del primer nombre de archivo dependiente (que puede ser un dependiente implícito). Componentes de nombre de archivo son unidad, ruta de acceso, nombre base y extensión tal como se especifica, el archivo no tal como existe en el disco. Use **%s** para representar el nombre de archivo completo. Use **%&#124;**[*elementos*]**F** (una barra vertical el signo de porcentaje) para representar las partes del nombre de archivo, donde *elementos*puede ser cero o más de las siguientes letras, en cualquier orden.  
  
|Carta|Descripción|  
|------------|-----------------|  
|No hay ninguna letra|Nombre completo (igual que **%s**)|  
|**d**|Unidad|  
|**p**|Ruta de acceso|  
|**f**|Nombre base del archivo|  
|**e**|Extensión de archivo|  
  
 Por ejemplo, si el nombre de archivo es c:\prog.exe:  
  
-   %s será c:\prog.exe  
  
-   %&#124;F será c:\prog.exe  
  
-   %&#124;dF será c  
  
-   %&#124;pF será c:\  
  
-   %&#124;fF será programa  
  
-   %&#124;eF será exe  
  
## <a name="see-also"></a>Vea también  
 [Comandos en un archivo MAKE](../build/commands-in-a-makefile.md)