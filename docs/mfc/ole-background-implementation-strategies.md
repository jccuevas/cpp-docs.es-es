---
title: 'Nociones de OLE: Estrategias de implementación'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE [MFC], development strategy
- OLE applications [MFC], implementing OLE
- applications [OLE], implementing OLE
ms.assetid: 0875ddae-99df-488c-82c6-164074a81058
ms.openlocfilehash: a9bcbc16b08f16953df92efe5a83db39f9a33cc5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50624398"
---
# <a name="ole-background-implementation-strategies"></a>Nociones de OLE: Estrategias de implementación

Dependiendo de la aplicación, hay cuatro estrategias de implementación posibles para agregar compatibilidad con OLE:

- Se escribe una nueva aplicación.

   Esta situación suele requerir menos trabajo. Ejecute al Asistente para aplicaciones MFC y seleccione características avanzadas o compatibilidad con documentos compuestos para crear una aplicación esqueleto. Para obtener información sobre estas opciones y sus funciones, vea el artículo [crear un programa EXE de MFC](../mfc/reference/mfc-application-wizard.md).

- Tiene un programa escrito con la biblioteca Microsoft Foundation Class versión 2.0 o superior que no es compatible con OLE.

   Cree una nueva aplicación con MFC Application Wizard, como se mencionó anteriormente y, a continuación, copie y pegue el código de la nueva aplicación en la aplicación existente. Esto funcionará para servidores, contenedores o aplicaciones automatizadas. Consulte la MFC [SCRIBBLE](../visual-cpp-samples.md) muestra un ejemplo de esta estrategia.

- Tiene un programa de Microsoft Foundation Class Library que implementa la compatibilidad con la versión 1.0 de OLE.

   Consulte [41 Nota técnica de MFC](../mfc/tn041-mfc-ole1-migration-to-mfc-ole-2.md) para esta estrategia de conversión.

- Tiene una aplicación que no se escribió utilizando Microsoft Foundation Classes y que puede o no ha implementado compatibilidad con OLE.

   Esta situación requiere más trabajo. Un enfoque consiste en crear una nueva aplicación, como se muestra en la primera estrategia y, a continuación, copie y pegue el código existente en él. Si el código existente está escrito en C, es posible que deba modificarlo para poder compilarlo como código de C++. Si el código de C llama a la API de Windows, no es necesario cambiarlo para utilizar Microsoft Foundation classes. Este enfoque probablemente requerirá cierta reestructuración del programa para admitir la arquitectura documento/vista que se usaba en las versiones 2.0 y versiones posteriores de Microsoft Foundation Classes. Para obtener más información acerca de esta arquitectura, consulte [Nota técnica 25](../mfc/tn025-document-view-and-frame-creation.md).

Una vez que haya decidido una estrategia, debe leer la [contenedores](../mfc/containers.md) o [servidores](../mfc/servers.md) artículos (según el tipo de aplicación que está escribiendo) o examinar los programas de ejemplo, o ambos. Los ejemplos OLE de MFC [OCLIENT](../visual-cpp-samples.md) y [HIERSVR](../visual-cpp-samples.md) muestran cómo implementar los distintos aspectos de los contenedores y servidores, respectivamente. En varios puntos a lo largo de estos artículos, hará referencia a determinadas funciones de estas aplicaciones como ejemplos de las técnicas que se está analizando.

## <a name="see-also"></a>Vea también

[Nociones de OLE](../mfc/ole-background.md)<br/>
[Contenedores: Implementar un contenedor](../mfc/containers-implementing-a-container.md)<br/>
[Servidores: Implementar un servidor](../mfc/servers-implementing-a-server.md)<br/>
[Asistente para aplicaciones MFC](../mfc/reference/mfc-application-wizard.md)

