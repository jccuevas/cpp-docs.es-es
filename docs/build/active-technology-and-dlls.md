---
title: "Tecnología activa y archivos DLL | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- in-process server DLLs
- Automation [C++], DLLs
- DLLs [C++], Active Technology
- Active technology [C++]
- MFC DLLs [C++], Active Technology
ms.assetid: 3ed27f8d-164a-4562-ad61-9f2333404cc7
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 44dcc58aed4025af2e3e2177e978633c13f0ef20
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="active-technology-and-dlls"></a>Tecnología activa y archivos DLL
Tecnología activa permite a los servidores de objetos implementarse completamente dentro de un archivo DLL. Este tipo de servidor se llama a un servidor en proceso. MFC no compatibilidad total con servidores en proceso para todas las características de edición visual, principalmente porque la tecnología activa no proporciona una forma de un servidor para enlazar al bucle de mensajes principal del contenedor. MFC requiere acceso al bucle de mensajes de la aplicación contenedora para controlar el procesamiento de tiempo de inactividad y teclas de aceleración.  
  
 Si está escribiendo un servidor de automatización y el servidor no tiene ninguna interfaz de usuario, puede convertir al servidor en un servidor en proceso y colocarlo en un archivo DLL.  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?  
  
-   [Servidores de automatización](../mfc/automation-servers.md)  
  
## <a name="see-also"></a>Vea también  
 [Archivos DLL en Visual C++](../build/dlls-in-visual-cpp.md)