---
title: Tecnología activa y archivos DLL
ms.date: 11/04/2016
helpviewer_keywords:
- in-process server DLLs
- Automation [C++], DLLs
- DLLs [C++], Active Technology
- Active technology [C++]
- MFC DLLs [C++], Active Technology
ms.assetid: 3ed27f8d-164a-4562-ad61-9f2333404cc7
ms.openlocfilehash: 270c64df9af792a73acf1ad408aca02e7fadc30f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50535816"
---
# <a name="active-technology-and-dlls"></a>Tecnología activa y archivos DLL

Tecnología activa permite a los servidores de objetos implementarse completamente dentro de un archivo DLL. Este tipo de servidor se llama a un servidor en proceso. MFC no admite completamente los servidores en proceso para todas las características de edición visual, principalmente porque la tecnología activa no proporciona una forma de un servidor conectar el bucle de mensajes principal del contenedor. MFC requiere acceso al bucle de mensajes de la aplicación contenedora para controlar las teclas de aceleración y tiempo de inactividad.

Si está escribiendo un servidor de automatización y el servidor no tiene ninguna interfaz de usuario, puede que a su servidor en un servidor en proceso y colocarlo en un archivo DLL.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

- [Servidores de automatización](../mfc/automation-servers.md)

## <a name="see-also"></a>Vea también

[Archivos DLL en Visual C++](../build/dlls-in-visual-cpp.md)