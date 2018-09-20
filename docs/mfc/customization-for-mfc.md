---
title: Personalización de MFC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- customizations, MFC Extensions
ms.assetid: 3b1b7532-8cc9-48dc-9bbe-7fd4060530b5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 640d6726623e8fb6d563153823f449f7caefcf30
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46385006"
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

