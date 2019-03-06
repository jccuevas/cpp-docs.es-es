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
ms.openlocfilehash: 82e18efe66350349c8cbef7f47b7d1fb226674f1
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57420172"
---
# <a name="active-technology-and-dlls"></a>Tecnología activa y archivos DLL

Tecnología activa permite a los servidores de objetos implementarse completamente dentro de un archivo DLL. Este tipo de servidor se llama a un servidor en proceso. MFC no admite completamente los servidores en proceso para todas las características de edición visual, principalmente porque la tecnología activa no proporciona una forma de un servidor conectar el bucle de mensajes principal del contenedor. MFC requiere acceso al bucle de mensajes de la aplicación contenedora para controlar las teclas de aceleración y tiempo de inactividad.

Si está escribiendo un servidor de automatización y el servidor no tiene ninguna interfaz de usuario, puede que a su servidor en un servidor en proceso y colocarlo en un archivo DLL.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

- [Servidores de automatización](../mfc/automation-servers.md)

## <a name="see-also"></a>Vea también

[Archivos DLL en Visual C++](../build/dlls-in-visual-cpp.md)
