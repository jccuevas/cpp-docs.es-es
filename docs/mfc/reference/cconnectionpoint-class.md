---
title: "CConnectionPoint Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CConnectionPoint"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CConnectionPoint class"
ms.assetid: f0f23a1e-5e8c-41a9-aa6c-1a4793b28e8f
caps.latest.revision: 20
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CConnectionPoint Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Define un tipo especial de interfaz se utiliza para comunicarse con otros objetos OLE, denominado “pin.”  
  
## Sintaxis  
  
```  
class CConnectionPoint : public CCmdTarget  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CConnectionPoint::CConnectionPoint](../Topic/CConnectionPoint::CConnectionPoint.md)|Crea un objeto `CConnectionPoint`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CConnectionPoint::GetConnections](../Topic/CConnectionPoint::GetConnections.md)|recupera todos los puntos de conexión en un mapa de la conexión.|  
|[CConnectionPoint::GetContainer](../Topic/CConnectionPoint::GetContainer.md)|Recupera el contenedor del control que posee la asignación de la conexión.|  
|[CConnectionPoint::GetIID](../Topic/CConnectionPoint::GetIID.md)|Recupera el identificador de interfaz de un punto de conexión.|  
|[CConnectionPoint::GetMaxConnections](../Topic/CConnectionPoint::GetMaxConnections.md)|recupera el número máximo de puntos de conexión admitidos por un control.|  
|[CConnectionPoint::GetNextConnection](../Topic/CConnectionPoint::GetNextConnection.md)|Recupera un puntero al elemento de la conexión en `pos`.|  
|[CConnectionPoint::GetStartPosition](../Topic/CConnectionPoint::GetStartPosition.md)|Inicie una iteración de mapa devuelve el valor de **POSICIÓN** que se puede pasar a una llamada de `GetNextConnection` .|  
|[CConnectionPoint::OnAdvise](../Topic/CConnectionPoint::OnAdvise.md)|Llamado por el marco al establecer o y conexiones.|  
|[CConnectionPoint::QuerySinkInterface](../Topic/CConnectionPoint::QuerySinkInterface.md)|Recupera un puntero a la interfaz solicitada de receptor.|  
  
## Comentarios  
 A diferencia de las interfaces VIEJAS normales, que se utilizan para implementar y exponer la funcionalidad de un control OLE, un punto de conexión implementa una interfaz de salida que puede iniciar acciones en otros objetos, como eventos bounce y notificaciones.  
  
 Una conexión consta de dos partes: el objeto que indica la interfaz, denominada “origen”, y el objeto que implementa la interfaz, llamado el “receptor.” Expone un punto de conexión, un origen permite que los receptores establecen conexiones a sí mismo.  A través del mecanismo de puntos de conexión, un objeto de origen obtiene un puntero a la implementación de receptor de un conjunto de funciones miembro.  Por ejemplo, para desencadenar un evento implementado por el receptor, el origen puede llamar al método correspondiente de la implementación de receptor.  
  
 de forma predeterminada, `COleControl`\- la clase derivada implementa dos puntos de conexión: uno de los eventos y otro para las notificaciones de cambio de propiedad.  Estas conexiones se utilizan, respectivamente, para el desencadenamiento de eventos y notificar a un receptor \(por ejemplo, el contenedor del control\) cuando un valor de propiedad ha cambiado.  Compatibilidad también se proporciona para que los controles OLE implementan los puntos de conexión adicionales.  Para cada punto de conexión adicional implementado en la clase de control, debe declarar una “parte de conexión” esa implementa el punto de conexión.  Si implementa uno o varios puntos de conexión, también debe declarar una sola “conexión asignada” en la clase de control.  
  
 El ejemplo siguiente se muestra una asignación simple de conexión y un punto de conexión para el control OLE de `Sample` , que consta de dos fragmentos de código: la primera parte declara el mapa y el punto de conexión; el segundo implementa este mapa y elija.  El primer fragmento se inserta en la declaración de clase de control, bajo la sección de `protected` :  
  
 [!code-cpp[NVC_MFCConnectionPoints#7](../../mfc/codesnippet/CPP/cconnectionpoint-class_1.h)]  
  
 Las macros de `BEGIN_CONNECTION_PART` y de `END_CONNECTION_PART` declare una clase incrustada, `XSampleConnPt` \(derivado de `CConnectionPoint`\) que implementan este punto de conexión determinado.  Si desea reemplazar cualquier funciones miembro de `CConnectionPoint` , o agregar funciones miembro dispone, declárela entre estas dos macros.  Por ejemplo, la macro de `CONNECTION_IID` reemplaza la función miembro de `CConnectionPoint::GetIID` cuando está colocada entre estas dos macros.  
  
 El segundo fragmento de código se inserta en el archivo de implementación \(.CPP\) de la clase de control.  Este código implementa la asignación de la conexión, que incluye el punto de conexión adicional, `SampleConnPt`:  
  
 [!code-cpp[NVC_MFCConnectionPoints#2](../../mfc/codesnippet/CPP/cconnectionpoint-class_2.cpp)]  
  
 Una vez que se han insertado estos fragmentos de código, el control OLE de ejemplo expone un punto de conexión para la interfaz de **ISampleSink** .  
  
 Normalmente, los puntos de conexión admiten la “conoce como multidifusión”, que es la capacidad de propagar a varios receptores conectados a la misma interfaz.  El fragmento de código siguiente muestra cómo realizar se conoce como multidifusión recorriendo en iteración cada receptor en un punto de conexión:  
  
 [!code-cpp[NVC_MFCConnectionPoints#4](../../mfc/codesnippet/CPP/cconnectionpoint-class_3.cpp)]  
  
 Este ejemplo recupera el conjunto actual de conexiones en el punto de conexión de `SampleConnPt` con una llamada a `CConnectionPoint::GetConnections`.  Después recorre en iteración las conexiones y llama a `ISampleSink::SinkFunc` en cada conexión activa.  
  
 Para obtener más información sobre cómo utilizar `CConnectionPoint`, vea el artículo [puntos de conexión](../../mfc/connection-points.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CConnectionPoint`  
  
## Requisitos  
 **encabezado:** afxdisp.h  
  
## Vea también  
 [CCmdTarget Class](../../mfc/reference/ccmdtarget-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)