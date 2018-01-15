---
title: COM EN MFC | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: MFC COM (MFC)
dev_langs: C++
helpviewer_keywords:
- MFC, COM support
- MFC ActiveX controls [MFC], COM support in MFC
- MFC COM [MFC]
- ActiveX controls [MFC], COM object model
- Active technology [MFC]
- COM [MFC], MFC support
ms.assetid: 7646bdcb-3a06-4ed5-9386-9b00f3979dcb
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 827bef034eeb7fc46b397c50f5ddf0c4cb6e48fc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-com"></a>MFC COM
Un subconjunto de MFC está diseñado para ofrecer compatibilidad con COM, mientras que la mayoría de Active Template Library (ATL) está diseñado para la programación COM. Temas de esta sección describe la compatibilidad con de MFC COM.  
  
 Las tecnologías activas (como ActiveX controles, contención de documentos activos, OLE y así sucesivamente) usan el modelo de objetos componentes (COM) para habilitar los componentes de software interactuar entre sí en un entorno de red, independientemente del lenguaje con el que se encontraban creado. Tecnologías activas se pueden utilizar para crear aplicaciones que se ejecutan en el escritorio o en Internet. Para obtener más información, consulte [Introducción a COM](../atl/introduction-to-com.md) o [el modelo de objetos de componentes](http://msdn.microsoft.com/library/windows/desktop/ms694363).  
  
 Las tecnologías activas incluyen tecnologías de cliente y servidor, incluyendo las siguientes:  
  
-   [Contención de documentos activos](../mfc/active-document-containment.md), incluida en MFC versión 4.2 y versiones posteriores, permite a los usuarios ver [documentos activos](../mfc/active-documents.md) (por ejemplo, archivos de Microsoft Excel o Word) y activar toda la interfaz de nativo del documento aplicación de toda el área cliente de un [contenedor de documentos activos](../mfc/active-document-containers.md) como el cuaderno de Microsoft Office o Microsoft Internet Explorer. Los contenedores actúan como clientes, mientras que los documentos se proporcionan con [servidores de documentos activos](../mfc/active-document-servers.md). Para obtener más información sobre el uso de documentos activos en aplicaciones de Internet, consulte: [documentos activos en Internet](../mfc/active-documents-on-the-internet.md).  
  
-   Controles ActiveX son objetos interactivos que se pueden utilizar en contenedores como un sitio Web. Para obtener más información sobre los controles ActiveX, vea:  
  
    -   [Controles ActiveX MFC](../mfc/mfc-activex-controls.md)  
  
    -   [Controles ActiveX en Internet](../mfc/activex-controls-on-the-internet.md)  
  
    -   [Información general: Internet](../mfc/mfc-internet-programming-basics.md)  
  
    -   [Actualizar un ActiveX Control existente para usarlo en Internet](../mfc/upgrading-an-existing-activex-control.md)  
  
    -   [Depurar un Control ActiveX](/visualstudio/debugger/how-to-debug-an-activex-control)  
  
-   Active scripting controla el comportamiento integrado de uno o más controles ActiveX desde un explorador o el servidor. Para obtener más información sobre secuencias de comandos activas, vea [tecnología activa en Internet](../mfc/active-technology-on-the-internet.md).  
  
-   [Automatización](../mfc/automation.md) (anteriormente conocida como automatización OLE) permite a una aplicación para manipular objetos implementados en otra aplicación o "exponer" objetos de forma que se puedan manipular.  
  
     El objeto automatizado puede ser local o [remoto](../mfc/remote-automation.md) (en otra máquina accesible a través de una red). La automatización está disponible para objetos COM y OLE.  
  
-   En esta sección también proporciona información sobre cómo escribir componentes COM mediante MFC, por ejemplo, en [puntos de conexión](../mfc/connection-points.md).  
  
 Para obtener una explicación de lo que se sigue llamando OLE frente a lo que se denomina ahora tecnología activa, vea los temas sobre [OLE](../mfc/ole-in-mfc.md).  
  
 Además, vea el artículo de Knowledge Base Q248019: Cómo: evitar que servidor ocupado diálogo cuadro desde que aparecen durante unos COM operación larga.  
  
## <a name="in-this-section"></a>En esta sección  
 [Contención de documentos activos](../mfc/active-document-containment.md)  
  
 [Automatización](../mfc/automation.md)  
  
 [Automatización remota](../mfc/remote-automation.md)  
  
 [Puntos de conexión](../mfc/connection-points.md)  
  
 [Controles ActiveX MFC](../mfc/mfc-activex-controls.md)  
  
## <a name="see-also"></a>Vea también  
 [Conceptos](../mfc/mfc-concepts.md)

