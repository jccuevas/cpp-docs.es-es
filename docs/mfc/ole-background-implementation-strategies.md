---
title: 'Nociones de OLE: Estrategias de implementación'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE [MFC], development strategy
- OLE applications [MFC], implementing OLE
- applications [OLE], implementing OLE
ms.assetid: 0875ddae-99df-488c-82c6-164074a81058
ms.openlocfilehash: 90517f9b37872dd7de0ce1a2d08da94c93e6f8f8
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619897"
---
# <a name="ole-background-implementation-strategies"></a>Nociones de OLE: Estrategias de implementación

Dependiendo de la aplicación, hay cuatro posibles estrategias de implementación para agregar compatibilidad con OLE:

- Está escribiendo una nueva aplicación.

   Normalmente, esta situación requiere menos trabajo. Ejecute el Asistente para aplicaciones MFC y seleccione características avanzadas o compatibilidad con documentos compuestos para crear una aplicación de esqueleto. Para obtener información sobre estas opciones y lo que hacen, vea el artículo [crear un programa exe de MFC](reference/mfc-application-wizard.md).

- Tiene un programa escrito con la biblioteca MFC versión 2,0 o posterior que no admite OLE.

   Cree una nueva aplicación con el Asistente para aplicaciones MFC tal y como se mencionó anteriormente y, a continuación, copie y pegue el código de la nueva aplicación en la aplicación existente. Esto funcionará para servidores, contenedores o aplicaciones automatizadas. Vea el ejemplo [Scribble](../overview/visual-cpp-samples.md) de MFC para obtener un ejemplo de esta estrategia.

- Dispone de un programa biblioteca MFC que implementa la compatibilidad con la versión 1,0 de OLE.

   Vea la [Nota técnica 41 de MFC](tn041-mfc-ole1-migration-to-mfc-ole-2.md) para esta estrategia de conversión.

- Tiene una aplicación que no se ha escrito con el Microsoft Foundation Classes y que puede o no haber implementado la compatibilidad con OLE.

   Esta situación requiere la mayor parte del trabajo. Un enfoque consiste en crear una nueva aplicación, como en la primera estrategia, y después copiar y pegar el código existente en ella. Si el código existente se escribe en C, puede que tenga que modificarlo para que se pueda compilar como código de C++. Si el código de C llama a la API de Windows, no es necesario cambiarla para usar Microsoft Foundation Classes. Este enfoque probablemente requerirá alguna reestructuración del programa para admitir la arquitectura de documento/vista utilizada por las versiones 2,0 y posteriores del Microsoft Foundation Classes. Para obtener más información sobre esta arquitectura, vea la [Nota técnica 25](tn025-document-view-and-frame-creation.md).

Una vez que haya decidido una estrategia, debe leer los artículos sobre los [contenedores](containers.md) o [los servidores](servers.md) (según el tipo de aplicación que esté escribiendo) o examinar los programas de ejemplo, o ambos. Los ejemplos OLE de MFC [OCLIENT](../overview/visual-cpp-samples.md) y [HIERSVR](../overview/visual-cpp-samples.md) muestran cómo implementar los distintos aspectos de los contenedores y servidores, respectivamente. En varios puntos de estos artículos, se hará referencia a determinadas funciones de estos ejemplos como ejemplos de las técnicas que se tratan.

## <a name="see-also"></a>Consulte también

[Nociones de OLE](ole-background.md)<br/>
[Contenedores: Implementar un contenedor](containers-implementing-a-container.md)<br/>
[Servidores: Implementar un servidor](servers-implementing-a-server.md)<br/>
[Asistente para aplicaciones MFC](reference/mfc-application-wizard.md)
