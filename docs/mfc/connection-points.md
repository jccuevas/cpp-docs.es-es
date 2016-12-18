---
title: "Puntos de conexi&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IConnectionPoint"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CCmdTarget (clase), y puntos de conexión"
  - "COM, puntos de conexión"
  - "puntos de conexión [C++]"
  - "conexiones, puntos de conexión"
  - "IConnectionPoint (interfaz)"
  - "interfaces, IConnectionPoint"
  - "MFC [C++], compatibilidad con COM"
  - "MFC COM, puntos de conexión"
  - "puntos de conexión OLE y COM"
  - "receptores, puntos de conexión"
ms.assetid: bc9fd7c7-8df6-4752-ac8c-0b177442c88d
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Puntos de conexi&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se explica cómo implementar puntos de conexión \(anteriormente conocido como puntos de conexión de OLE\) mediante las clases MFC `CCmdTarget` y `CConnectionPoint`.  
  
 En el pasado, el modelo de objetos componentes \(COM\) definió un mecanismo general \(**IUnknown::QueryInterface**\) que permitía que los objetos se y que expusieran funcionalidad en interfaces.  Sin embargo, un mecanismo correspondiente que le permita a los objetos expusieran su capacidad de llamar a interfaces específicas no definido.  Es decir, COM define cómo los punteros de entrada a los objetos \(punteros a las interfaces de ese objeto\) se controlaron, pero no tenía un modelo explícito para las interfaces de salida \(punteros el objeto contienen a otros objetos interfaces\).  COM tiene ahora un modelo, denominado puntos de conexión, que admite esta funcionalidad.  
  
 Una conexión tiene dos partes: el objeto que llama a la interfaz, denominada el origen, y el objeto que implementa la interfaz, denominada receptor.  Un punto de conexión es la interfaz que expone el origen.  Expone un punto de conexión, un origen permite que los receptores establecen conexiones a sí mismo \(el origen\).  A través del mecanismo de puntos de conexión \(la interfaz de **IConnectionPoint** \), un puntero a la interfaz de receptor se pasa al objeto de origen.  Este puntero proporciona el origen con acceso a la implementación de receptor de un conjunto de funciones miembro.  Por ejemplo, para desencadenar un evento implementado por el receptor, el origen puede llamar al método correspondiente de la implementación de receptor.  La ilustración siguiente se muestra el punto de conexión descrito.  
  
 ![Punto de conexión implementado](../mfc/media/vc37lh1.png "vc37LH1")  
Un punto de conexión implementado  
  
 MFC implementa este modelo en las clases de [CConnectionPoint](../mfc/reference/cconnectionpoint-class.md) y de [CCmdTarget](../mfc/reference/ccmdtarget-class.md) .  Las clases derivadas de **CConnectionPoint** implementan la interfaz de **IConnectionPoint** , utilizada para exponer los puntos de conexión a otros objetos.  Las clases derivadas de `CCmdTarget` implementan la interfaz de **IConnectionPointContainer** , que puede enumerar todos los puntos de conexión disponible de un objeto o encuentra un punto de conexión concreto.  
  
 Para cada punto de conexión implementado en la clase, debe declarar una parte de la conexión que implementa el punto de conexión.  Si implementa uno o varios puntos de conexión, también debe declarar una sola conexión asignada en la clase.  Un mapa de conexión es una tabla de puntos de conexión admitidos por el control ActiveX.  
  
 Los ejemplos siguientes muestran un mapa simple de conexión y un punto de conexión.  El primer ejemplo declara el mapa y el punto de conexión; el segundo ejemplo implementa el mapa y elija.  Observe que `CMyClass` debe ser `CCmdTarget`\- clase derivada.  En el primer ejemplo, el código se inserta en la declaración de clase, bajo la sección de **protegido** :  
  
 [!code-cpp[NVC_MFCConnectionPoints#1](../mfc/codesnippet/CPP/connection-points_1.h)]  
  
 `BEGIN_CONNECTION_PART` y macros de **END\_CONNECTION\_PART** declare una clase incrustada, `XSampleConnPt` \(derivado de `CConnectionPoint`\), que implementa este punto de conexión determinado.  Si desea reemplazar cualquier funciones miembro de `CConnectionPoint` o para agregar funciones miembro dispone, declárela entre estas dos macros.  Por ejemplo, la macro de `CONNECTION_IID` reemplaza la función miembro de `CConnectionPoint::GetIID` cuando está colocada entre estas dos macros.  
  
 En el segundo ejemplo, se inserta código en el archivo de implementación del control \(archivo .cpp\).  Este código implementa la asignación de la conexión, que incluye el punto de conexión, `SampleConnPt`:  
  
 [!code-cpp[NVC_MFCConnectionPoints#2](../mfc/codesnippet/CPP/connection-points_2.cpp)]  
  
 Si la clase tiene más de un punto de conexión, inserte las macros adicionales de `CONNECTION_PART` entre `BEGIN_CONNECTION_MAP` y macros de `END_CONNECTION_MAP` .  
  
 Finalmente, agregue una llamada a `EnableConnections` en el constructor de clase.  Por ejemplo:  
  
 [!code-cpp[NVC_MFCConnectionPoints#3](../mfc/codesnippet/CPP/connection-points_3.cpp)]  
  
 Una vez que se ha insertado este código, `CCmdTarget`\- clase derivada expone un punto de conexión para la interfaz de **ISampleSink** .  La ilustración siguiente se muestra este ejemplo.  
  
 ![Punto de conexión implementado mediante MFC](../mfc/media/vc37lh2.png "vc37LH2")  
Un punto de Conexión implementado con MFC  
  
 Normalmente, los puntos de conexión admiten la “conoce como multidifusión” — la capacidad de propagar a varios receptores conectados a la misma interfaz.  El siguiente fragmento de ejemplo ilustra la forma de multidifusión recorriendo en iteración cada receptor en un punto de conexión:  
  
 [!code-cpp[NVC_MFCConnectionPoints#4](../mfc/codesnippet/CPP/connection-points_4.cpp)]  
  
 Este ejemplo recupera el conjunto actual de conexiones en el punto de conexión de `SampleConnPt` con una llamada a `CConnectionPoint::GetConnections`.  Después recorre en iteración las conexiones y llama a **ISampleSink::SinkFunc** en cada conexión activa.  
  
## Vea también  
 [MFC COM](../mfc/mfc-com.md)