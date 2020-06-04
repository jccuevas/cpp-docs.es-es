---
title: Personalización de MFC
ms.date: 11/04/2016
helpviewer_keywords:
- customizations, MFC Extensions
ms.assetid: 3b1b7532-8cc9-48dc-9bbe-7fd4060530b5
ms.openlocfilehash: 42f4b21fb257646d4d505427760a8fe1c7056e77
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62241698"
---
# <a name="customization-for-mfc"></a>Personalización de MFC

En este tema proporciona sugerencias para personalizar una aplicación MFC.

## <a name="general-customizations"></a>Personalizaciones generales

Puede guardar y cargar el estado de la aplicación en el registro. Cuando se habilita esta opción, la aplicación cargará su estado inicial del registro. Si cambia el diseño de acoplamiento inicial para la aplicación, tendrá que borrar los datos del registro para la aplicación. En caso contrario, los datos en el registro sobrescriben los cambios realizados en el diseño inicial.

## <a name="class-specific-customizations"></a>Personalizaciones específicas de la clase

Sugerencias de personalización adicional pueden encontrarse en los temas siguientes:

- [CBasePane (clase)](../mfc/reference/cbasepane-class.md)

- [CDockablePane (clase)](../mfc/reference/cdockablepane-class.md)

- [CDockingManager (clase)](../mfc/reference/cdockingmanager-class.md)

- [CMFCBaseTabCtrl (clase)](../mfc/reference/cmfcbasetabctrl-class.md)

## <a name="additional-customization-tips"></a>Sugerencias de personalización adicionales

[Personalización del teclado y del mouse](../mfc/keyboard-and-mouse-customization.md)

[Herramientas definidas por el usuario](../mfc/user-defined-tools.md)

## <a name="see-also"></a>Vea también

[Aplicaciones de escritorio de MFC](../mfc/mfc-desktop-applications.md)<br/>
[Implicaciones de seguridad de la personalización](../mfc/security-implications-of-customization.md)
