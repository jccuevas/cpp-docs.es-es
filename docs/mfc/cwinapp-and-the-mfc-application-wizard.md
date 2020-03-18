---
title: CWinApp y el Asistente para aplicaciones MFC
ms.date: 11/04/2016
helpviewer_keywords:
- application wizards [MFC], and CWinApp
- CWinApp class [MFC], and MFC Application Wizard
- MFC, wizards
ms.assetid: f8ac0491-3302-4e46-981d-0790624eb8a2
ms.openlocfilehash: 1a46842d7b4d6a588da585d63e2ad56982bb0ff8
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447040"
---
# <a name="cwinapp-and-the-mfc-application-wizard"></a>CWinApp y el Asistente para aplicaciones MFC

Cuando crea una aplicación de esqueleto, el Asistente para aplicaciones MFC declara una clase de aplicación derivada de [CWinApp](../mfc/reference/cwinapp-class.md). El Asistente para aplicaciones MFC también genera un archivo de implementación que contiene los elementos siguientes:

- Mapa de mensajes para la clase de aplicación.

- Constructor de clase vacía.

- Una variable que declara el único objeto de la clase.

- Implementación estándar de la función miembro `InitInstance`.

La clase de aplicación se coloca en el encabezado del proyecto y en los archivos de código fuente principales. Los nombres de la clase y los archivos creados se basan en el nombre de proyecto proporcionado en el Asistente para aplicaciones MFC. La forma más fácil de ver el código de estas clases es a través de [vista de clases](/visualstudio/ide/viewing-the-structure-of-code).

Las implementaciones estándar y el mapa de mensajes suministrados son adecuados para muchos propósitos, pero se pueden modificar según sea necesario. Las implementaciones más interesantes son las `InitInstance` función miembro. Normalmente, agregará código a la implementación del esqueleto de `InitInstance`.

## <a name="see-also"></a>Consulte también

[CWinApp: la clase Application](../mfc/cwinapp-the-application-class.md)<br/>
[Funciones miembro de CWinApp que se pueden sobrecargar](../mfc/overridable-cwinapp-member-functions.md)<br/>
[Servicios especiales de CWinApp](../mfc/special-cwinapp-services.md)
