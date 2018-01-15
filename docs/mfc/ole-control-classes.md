---
title: Clases de controles OLE | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.classes.ole
dev_langs: C++
helpviewer_keywords:
- ActiveX classes [MFC]
- custom controls [MFC], classes
- ActiveX controls [MFC], OLE control classes
- ActiveX control classes [MFC]
- OLE controls [MFC], classes
- OLE control classes [MFC]
- reusable component classes [MFC]
ms.assetid: 96495ec3-319e-4163-b839-1af0428ed9dd
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e61d0ca8ed269557efbd566da1aca160ef669e83
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="ole-control-classes"></a>Clases de controles OLE
Estas son las clases principales que utilizar al escribir controles OLE. El `COleControlModule` clase en un módulo de control OLE es como la [CWinApp](../mfc/reference/cwinapp-class.md) clase en una aplicación. Cada módulo implementa uno o más controles OLE; Estos controles se representan mediante `COleControl` objetos. Estos controles comunican con sus contenedores mediante `CConnectionPoint` objetos.  
  
 El `CPictureHolder` y `CFontHolder` clases encapsulan interfaces COM para imágenes y fuentes, mientras el `COlePropertyPage` y `CPropExchange` clases le ayudarán a implementar páginas de propiedades y persistencia de la propiedad para el control.  
  
 [COleControlModule](../mfc/reference/colecontrolmodule-class.md)  
 Reemplaza el `CWinApp` clase para el módulo de control OLE. Se deriva la `COleControlModule` clase para desarrollar un objeto de módulo de control OLE. Proporciona funciones miembro para inicializar el módulo del control OLE.  
  
 [COleControl](../mfc/reference/colecontrol-class.md)  
 Se deriva la `COleControl` clase para desarrollar un control OLE. Deriva `CWnd`, esta clase hereda toda la funcionalidad de un objeto de ventana de Windows además de funcionalidad específica de OLE, por ejemplo, la activación de eventos y la capacidad para admitir los métodos y propiedades.  
  
 [CConnectionPoint](../mfc/reference/cconnectionpoint-class.md)  
 La `CConnectionPoint` clase define un tipo especial de interfaz que se utiliza para comunicarse con otros objetos OLE, denominados punto de conexión. Un punto de conexión implementa una interfaz de salida que es capaz de iniciar acciones de otros objetos, como desencadenar eventos y notificaciones de cambio.  
  
 [CPictureHolder](../mfc/reference/cpictureholder-class.md)  
 Encapsula la funcionalidad de un objeto de imagen de Windows y el `IPicture` COM interfaz; usado para implementar la propiedad de imagen personalizada de un control OLE.  
  
 [CFontHolder](../mfc/reference/cfontholder-class.md)  
 Encapsula la funcionalidad de un objeto de fuente de Windows y el `IFont` COM interfaz; usado para implementar la propiedad Font estándar de un control OLE.  
  
 [COlePropertyPage](../mfc/reference/colepropertypage-class.md)  
 Muestra las propiedades de una OLE controlan en una interfaz gráfica, similar a un cuadro de diálogo.  
  
 [CPropExchange](../mfc/reference/cpropexchange-class.md)  
 Admite la implementación de persistencia de la propiedad para controles OLE. Análoga a [CDataExchange](../mfc/reference/cdataexchange-class.md) para cuadros de diálogo.  
  
 [CMonikerFile](../mfc/reference/cmonikerfile-class.md)  
 Toma un moniker o una representación de cadena que puede convertir en un moniker y enlaza de forma sincrónica en el flujo para el que el moniker es un nombre.  
  
 [CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md)  
 Funciona de forma similar a `CMonikerFile`; sin embargo, enlaza el moniker de forma asincrónica en la secuencia para la que el moniker es un nombre.  
  
 [CDataPathProperty](../mfc/reference/cdatapathproperty-class.md)  
 Implementa una propiedad de control OLE que se puede cargar de forma asincrónica.  
  
 [CCachedDataPathProperty](../mfc/reference/ccacheddatapathproperty-class.md)  
 Implementa una propiedad de control OLE transferida de forma asincrónica y almacenada en memoria caché en un archivo de memoria.  
  
 [COleCmdUI](../mfc/reference/colecmdui-class.md)  
 Permite que un documento activo recibir comandos que se originan en la interfaz de usuario de su contenedor (por ejemplo, FileNew, abrir, impresión etc.) y permite que un contenedor recibir comandos que se originan en la interfaz de usuario del documento activo.  
  
 [COleSafeArray](../mfc/reference/colesafearray-class.md)  
 Funciona con matrices de tipo y dimensión arbitrarios.  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../mfc/class-library-overview.md)

