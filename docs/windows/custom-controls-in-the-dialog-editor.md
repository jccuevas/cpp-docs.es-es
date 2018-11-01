---
title: Controles personalizados en el Editor de cuadro de diálogo (C++)
ms.date: 11/04/2016
f1_keywords:
- Custom Control
helpviewer_keywords:
- controls [C++], templates
- custom controls [C++], dialog boxes
- custom controls [C++]
- dialog box controls [C++], custom (user) controls
- Dialog Editor [C++], custom controls
ms.assetid: f494b314-4000-4bbe-bbd0-4b18fb71ede1
ms.openlocfilehash: c48ad87948037fa843fdc16a016ae23bf139feb1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50677102"
---
# <a name="custom-controls-in-the-dialog-editor-c"></a>Controles personalizados en el Editor de cuadro de diálogo (C++)

El editor de cuadro de diálogo permite usar existente "custom" o "" controles de usuario en una plantilla de cuadro de diálogo.

> [!NOTE]
> Controles personalizados en este sentido no son debe confundirse con los controles ActiveX. Controles ActiveX se denominan controles personalizados OLE. Además, no confunda estos controles con los controles dibujados por el propietario de Windows.

Esta funcionalidad está diseñada para permitir el uso de controles distintos de los proporcionados por Windows. En tiempo de ejecución, el control está asociado con una clase de ventana (no es el mismo que una clase de C++). Una manera más común para realizar la misma tarea consiste en instalar cualquier control, como un control estático, en el cuadro de diálogo. A continuación, en tiempo de ejecución, en el [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) funcione, quita el control y reemplazarlo con su propio control personalizado.

Esta es una técnica anterior. Hoy en día se recomienda en la mayoría de los casos a escribir un control ActiveX o una subclase de un control común de Windows.

Para estos controles personalizados, estará limitado a:

- Configuración de la ubicación en el cuadro de diálogo.

- Escriba un título.

- Que identifica el nombre de clase de Windows del control (el código de aplicación debe registrar el control con este nombre).

- Escriba un valor hexadecimal de 32 bits que establece el estilo del control.

- Establecer el estilo extendido.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Controles de cuadros de diálogo](../windows/controls-in-dialog-boxes.md)<br/>
[Controles](../mfc/controls-mfc.md)