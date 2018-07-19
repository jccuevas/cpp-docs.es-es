---
title: Tecnología activa y archivos DLL | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- in-process server DLLs
- Automation [C++], DLLs
- DLLs [C++], Active Technology
- Active technology [C++]
- MFC DLLs [C++], Active Technology
ms.assetid: 3ed27f8d-164a-4562-ad61-9f2333404cc7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f5e0296b994f7944d5b26e98ba1b0545a03ec55b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32360118"
---
# <a name="active-technology-and-dlls"></a>Tecnología activa y archivos DLL
Tecnología activa permite a los servidores de objetos implementarse completamente dentro de un archivo DLL. Este tipo de servidor se llama a un servidor en proceso. MFC no compatibilidad total con servidores en proceso para todas las características de edición visual, principalmente porque la tecnología activa no proporciona una forma de un servidor para enlazar al bucle de mensajes principal del contenedor. MFC requiere acceso al bucle de mensajes de la aplicación contenedora para controlar el procesamiento de tiempo de inactividad y teclas de aceleración.  
  
 Si está escribiendo un servidor de automatización y el servidor no tiene ninguna interfaz de usuario, puede convertir al servidor en un servidor en proceso y colocarlo en un archivo DLL.  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?  
  
-   [Servidores de automatización](../mfc/automation-servers.md)  
  
## <a name="see-also"></a>Vea también  
 [Archivos DLL en Visual C++](../build/dlls-in-visual-cpp.md)