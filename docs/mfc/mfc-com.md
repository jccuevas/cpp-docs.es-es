---
title: COM EN MFC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- MFC COM (MFC)
dev_langs:
- C++
helpviewer_keywords:
- MFC, COM support
- MFC ActiveX controls [MFC], COM support in MFC
- MFC COM [MFC]
- ActiveX controls [MFC], COM object model
- Active technology [MFC]
- COM [MFC], MFC support
ms.assetid: 7646bdcb-3a06-4ed5-9386-9b00f3979dcb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3e8c3af361e1ffb5928132727fa124f03a99e81e
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43205654"
---
# <a name="mfc-com"></a>MFC COM
Un subconjunto de MFC está diseñado para ofrecer compatibilidad con COM, aunque la mayoría de Active Template Library (ATL) está diseñado para la programación COM. Temas de esta sección describe la compatibilidad con de MFC COM.  
  
 Tecnologías activas (como ActiveX controles, contención de documentos activos, OLE y así sucesivamente) usan el modelo de objetos componentes (COM) para habilitar los componentes de software interactuar entre sí en un entorno de red, independientemente del lenguaje con el que fueran creado. Tecnologías activas pueden utilizarse para crear aplicaciones que se ejecutan en el escritorio o en Internet. Para obtener más información, consulte [Introducción a COM](../atl/introduction-to-com.md) o [el modelo de objetos componentes](/windows/desktop/com/the-component-object-model).  
  
 Tecnologías activas incluyen tecnologías de cliente y servidor, incluido lo siguiente:  
  
-   [Contención de documentos activos](../mfc/active-document-containment.md), incluida en MFC versión 4.2 y versiones posteriores, permite a los usuarios ver [documentos activos](../mfc/active-documents.md) (como archivos de Microsoft Excel o Word) y activar toda la interfaz de nativo del documento aplicación en el área de cliente completa de un [contenedor de documentos activos](../mfc/active-document-containers.md) como el cuaderno de Microsoft Office o Microsoft Internet Explorer. Los contenedores que actúan como clientes, mientras que los documentos se proporcionan por [servidores de documentos activos](../mfc/active-document-servers.md). Para obtener más información sobre el uso de documentos activos en las aplicaciones de Internet, consulte: [documentos activos en Internet](../mfc/active-documents-on-the-internet.md).  
  
-   Controles ActiveX son objetos interactivos que se pueden utilizar en contenedores como un sitio Web. Para obtener más información sobre los controles ActiveX, vea:  
  
    -   [Controles ActiveX MFC](../mfc/mfc-activex-controls.md)  
  
    -   [Controles ActiveX en Internet](../mfc/activex-controls-on-the-internet.md)  
  
    -   [Información general: Internet](../mfc/mfc-internet-programming-basics.md)  
  
    -   [Actualizar un ActiveX Control existente que se usará en Internet](../mfc/upgrading-an-existing-activex-control.md)  
  
    -   [Depurar un Control ActiveX](/visualstudio/debugger/how-to-debug-an-activex-control)  
  
-   Active scripting controla el comportamiento integrado de uno o varios controles ActiveX desde un explorador o el servidor. Para obtener más información sobre secuencias de comandos ActiveX, vea [tecnología activa en Internet](../mfc/active-technology-on-the-internet.md).  
  
-   [Automatización](../mfc/automation.md) (anteriormente conocida como automatización OLE) permite que una aplicación manipule objetos implementados en otra aplicación o "exponer" objetos de forma que se puedan manipular.  
  
     El objeto automatizado puede ser local o remoto (en otra máquina accesible a través de una red). La automatización está disponible para objetos COM y OLE.  
  
-   En esta sección también proporciona información sobre cómo escribir componentes COM mediante MFC, por ejemplo, en [puntos de conexión](../mfc/connection-points.md).  
  
 Para obtener una explicación de lo que todavía se denomina OLE en comparación con lo que ahora se denomina tecnología activa, vea los temas sobre [OLE](../mfc/ole-in-mfc.md).  
  
 Además, consulte el artículo de Knowledge Base Q248019: HOWTO: evitar que servidor ocupado diálogo cuadro desde que aparecen durante unas COM operación de larga duración.  
  
## <a name="in-this-section"></a>En esta sección  
 [Contención de documentos activos](../mfc/active-document-containment.md)  
  
 [Automatización](../mfc/automation.md)  
  
 [Puntos de conexión](../mfc/connection-points.md)  
  
 [Controles ActiveX MFC](../mfc/mfc-activex-controls.md)  
  
## <a name="see-also"></a>Vea también  
 [Conceptos](../mfc/mfc-concepts.md)

