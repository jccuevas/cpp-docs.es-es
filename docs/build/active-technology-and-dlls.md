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
ms.openlocfilehash: f67fb9548601ac705ceda08d20d3049f0bf1e0a5
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221002"
---
# <a name="active-technology-and-dlls"></a>Tecnología activa y archivos DLL

Tecnología activa permite a los servidores de objetos implementarse completamente dentro de un archivo DLL. Este tipo de servidor se denomina servidor en proceso. MFC no es totalmente compatible con servidores en proceso para todas las características de edición visual, principalmente porque Tecnología activa no proporciona una manera de que un servidor se conecte con el bucle de mensajes principal del contenedor. MFC requiere acceso al bucle de mensajes de la aplicación contenedora para controlar las teclas de aceleración y el procesamiento de los tiempos de inactividad.

Si está escribiendo un servidor de automatización y el servidor no tiene ninguna interfaz de usuario, puede convertirlo en un servidor de proceso y colocarlo al completo en un archivo DLL.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

- [Servidores de automatización](../mfc/automation-servers.md)

## <a name="see-also"></a>Vea también

[Creación de archivos DLL de C/C++ en Visual Studio](dlls-in-visual-cpp.md)
