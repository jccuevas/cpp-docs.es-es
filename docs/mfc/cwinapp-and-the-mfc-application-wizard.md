---
title: CWinApp y el Asistente para aplicaciones MFC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CWinApp
dev_langs:
- C++
helpviewer_keywords:
- application wizards [MFC], and CWinApp
- CWinApp class [MFC], and MFC Application Wizard
- MFC, wizards
ms.assetid: f8ac0491-3302-4e46-981d-0790624eb8a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 009126061856d1165e5d08f6ecc4bd2e7745f2fd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46382965"
---
# <a name="cwinapp-and-the-mfc-application-wizard"></a>CWinApp y el Asistente para aplicaciones MFC

Cuando crea una aplicación de esqueleto, MFC Application Wizard declara una clase de aplicación derivada de [CWinApp](../mfc/reference/cwinapp-class.md). El Asistente para aplicaciones MFC también genera un archivo de implementación que contiene los siguientes elementos:

- Un mapa de mensajes para la clase de aplicación.

- Un constructor de clase vacía.

- Una variable que declara sólo es objeto de la clase.

- Una implementación estándar de su `InitInstance` función miembro.

La clase de aplicación se coloca en el encabezado del proyecto y los archivos de código fuente principal. Los nombres de la clase y los archivos creados se basan en el nombre del proyecto que proporcione en MFC Application Wizard. La manera más fácil de ver el código de estas clases es a través de [vista de clases](/visualstudio/ide/viewing-the-structure-of-code).

Las implementaciones estándar y el mapa de mensajes proporcionados son adecuados para muchos propósitos, pero puede modificar según sea necesario. Es el más interesante de estas implementaciones el `InitInstance` función miembro. Normalmente, agregará código a la implementación básica de `InitInstance`.

## <a name="see-also"></a>Vea también

[CWinApp: la clase Application](../mfc/cwinapp-the-application-class.md)<br/>
[Funciones miembro de CWinApp que se pueden sobrecargar](../mfc/overridable-cwinapp-member-functions.md)<br/>
[Servicios especiales de CWinApp](../mfc/special-cwinapp-services.md)

