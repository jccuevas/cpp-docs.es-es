---
title: Personalización de MFC
ms.date: 11/04/2016
helpviewer_keywords:
- customizations, MFC Extensions
ms.assetid: 3b1b7532-8cc9-48dc-9bbe-7fd4060530b5
ms.openlocfilehash: 3b7597c3709ed700e82af94c78450ee5aff2d99b
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622970"
---
# <a name="customization-for-mfc"></a>Personalización de MFC

En este tema se proporcionan sugerencias para personalizar una aplicación MFC.

## <a name="general-customizations"></a>Personalizaciones generales

Puede guardar y cargar el estado de la aplicación en el registro. Cuando se habilita esta opción, la aplicación carga su estado inicial desde el registro. Si cambia el diseño de acoplamiento inicial de la aplicación, tendrá que borrar los datos del registro de la aplicación. De lo contrario, los datos del registro invalidarán los cambios realizados en el diseño inicial.

## <a name="class-specific-customizations"></a>Personalizaciones específicas de la clase

En los temas siguientes encontrará más sugerencias de personalización:

- [CBasePane (clase)](reference/cbasepane-class.md)

- [CDockablePane Class](reference/cdockablepane-class.md)

- [CDockingManager (clase)](reference/cdockingmanager-class.md)

- [CMFCBaseTabCtrl Class](reference/cmfcbasetabctrl-class.md)

## <a name="additional-customization-tips"></a>Sugerencias de personalización adicionales

[Personalización del teclado y del mouse](keyboard-and-mouse-customization.md)

[Herramientas definidas por el usuario](user-defined-tools.md)

## <a name="see-also"></a>Consulte también

[Aplicaciones de escritorio de MFC](mfc-desktop-applications.md)<br/>
[Implicaciones de seguridad de la personalización](security-implications-of-customization.md)
