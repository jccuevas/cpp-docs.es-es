---
title: "Clases de controles OLE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.classes.ole"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX (clases) [C++]"
  - "ActiveX (clases de controles) [C++]"
  - "controles ActiveX [C++], clases de controles OLE"
  - "controles personalizados [MFC], clases"
  - "clases de controles OLE [C++]"
  - "controles OLE [C++], clases"
  - "clases de componentes reutilizables"
ms.assetid: 96495ec3-319e-4163-b839-1af0428ed9dd
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Clases de controles OLE
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Éstas son las clases principales que se utilizan para escribir controles OLE.  La clase de `COleControlModule` en un módulo de controles activex es como la clase de [CWinApp](../mfc/reference/cwinapp-class.md) en una aplicación.  Cada módulo implementa uno o más controles OLE; estos controles se representan mediante objetos de `COleControl` .  Estos controles se comunican con sus contenedores mediante los objetos de `CConnectionPoint` .  
  
 Las clases de `CPictureHolder` y de `CFontHolder` encapsulan las interfaces COM para las imágenes y las fuentes, mientras que la ayuda de las clases de `COlePropertyPage` y de `CPropExchange` implementa las páginas de propiedades y la persistencia de propiedades del control.  
  
 [COleControlModule](../mfc/reference/colecontrolmodule-class.md)  
 Reemplaza la clase de `CWinApp` para el módulo de controles activex.  Derive de la clase de `COleControlModule` para desarrollar un objeto agente de controles activex.  Proporciona funciones miembro para el módulo de controles activex que se inicializa.  
  
 [COleControl](../mfc/reference/colecontrol-class.md)  
 Derive de la clase de `COleControl` para desarrollar un control OLE.  Derivado de `CWnd`, esta clase hereda toda la funcionalidad de un objeto de la ventana de Windows más funcionalidad OLE\- específica adicional, como desencadenamiento de eventos y la capacidad de admitir métodos y propiedades.  
  
 [CConnectionPoint](../mfc/reference/cconnectionpoint-class.md)  
 La clase de `CConnectionPoint` define un tipo especial de interfaz se utiliza para comunicarse con otros objetos OLE, denominado punto de conexión.  Un punto de conexión implementa una interfaz de salida que puede iniciar acciones en otros objetos, como eventos bounce y notificaciones.  
  
 [CPictureHolder](../mfc/reference/cpictureholder-class.md)  
 Encapsula la funcionalidad de un objeto de imagen de Windows y de la interfaz COM de `IPicture` ; se utiliza para implementar la propiedad de imagen personalizada de un control OLE.  
  
 [CFontHolder](../mfc/reference/cfontholder-class.md)  
 Encapsula la funcionalidad de un objeto de fuente de Windows y de la interfaz COM de `IFont` ; se utiliza para implementar la propiedad de fuente común de un control activex.  
  
 [COlePropertyPage](../mfc/reference/colepropertypage-class.md)  
 Muestra las propiedades de un control OLE en una interfaz gráfica, a un cuadro de diálogo.  
  
 [CPropExchange](../mfc/reference/cpropexchange-class.md)  
 Admite la implementación de persistencia de propiedad para los controles OLE.  Análogo a [CDataExchange](../mfc/reference/cdataexchange-class.md) para los cuadros de diálogo.  
  
 [CMonikerFile](../mfc/reference/cmonikerfile-class.md)  
 Toma un moniker, o una representación de cadena que puede crear en un moniker, y enlazarlo sincrónicamente a la secuencia de la que el moniker es un nombre.  
  
 [CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md)  
 Funciona de forma similar a `CMonikerFile`; sin embargo, enlaza el moniker de forma asincrónica a la secuencia de la que el moniker es un nombre.  
  
 [CDataPathProperty](../mfc/reference/cdatapathproperty-class.md)  
 Implementa una propiedad de control OLE que se puede cargar de forma asincrónica.  
  
 [CCachedDataPathProperty](../mfc/reference/ccacheddatapathproperty-class.md)  
 Implementa una propiedad de control OLE transferida de forma asincrónica y almacenada en memoria caché en un archivo de memoria.  
  
 [COleCmdUI](../mfc/reference/colecmdui-class.md)  
 Permite un documento activo reciba los comandos que se originan en la interfaz de usuario de su contenedor \(como FileNew, abra, imprimir, etc.\), y permite un contenedor que reciba los comandos que se originan en la interfaz de usuario del documento activo.  
  
 [COleSafeArray](../mfc/reference/colesafearray-class.md)  
 Funciona con matrices del tipo y la dimensión arbitrarios.  
  
## Vea también  
 [Información general de clases](../mfc/class-library-overview.md)