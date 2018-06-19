---
title: Puntos de conexión | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- IConnectionPoint
dev_langs:
- C++
helpviewer_keywords:
- IConnectionPoint interface
- connections, connection points
- OLE COM connection points
- MFC COM, connection points
- COM, connection points
- interfaces, IConnectionPoint
- MFC, COM support
- connection points [MFC]
- CCmdTarget class [MFC], and connection points
- sinks, connection points
ms.assetid: bc9fd7c7-8df6-4752-ac8c-0b177442c88d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 56686fe4ea2920f9365b84ec3064df4be95f4a3b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33346427"
---
# <a name="connection-points"></a>Puntos de conexión
Este artículo explica cómo implementar puntos de conexión (que antes de que se conocía como puntos de conexión OLE) mediante las clases MFC `CCmdTarget` y `CConnectionPoint`.  
  
 En el pasado, el modelo de objetos componentes (COM) define un mecanismo general (**IUnknown:: QueryInterface**) que permite implementar y exponer la funcionalidad en las interfaces de los objetos. Sin embargo, no se definió un mecanismo correspondiente que permitiera a los objetos exponer su capacidad para llamar a interfaces específicas. Es decir, COM define cómo entrantes punteros a objetos se controlaron (punteros a las interfaces del objeto), pero no tenía un modelo explícito para las interfaces salientes (punteros que contiene el objeto a interfaces de otros objetos). COM tiene ahora un modelo, denominado puntos de conexión, que es compatible con esta funcionalidad.  
  
 Una conexión tiene dos partes: el objeto de una llamada a la interfaz, denominada el origen y el objeto que implementa la interfaz, denominada receptor. Un punto de conexión es la interfaz expuesta por el origen. Al exponer un punto de conexión, un origen permite a los receptores establecer conexiones a sí mismo (origen). A través de la conexión de punto mecanismo (la **IConnectionPoint** interfaz), un puntero a la interfaz del receptor se pasa al objeto de origen. This (puntero) proporciona el origen con acceso a la implementación del receptor de un conjunto de funciones miembro. Por ejemplo, para desencadenar un evento implementado por el receptor, el origen puede llamar al método correspondiente de la implementación del receptor. La siguiente ilustración muestra la conexión punto descrito anteriormente.  
  
 ![Implementa el punto de conexión](../mfc/media/vc37lh1.gif "vc37lh1")  
Un punto de conexión implementado  
  
 MFC implementa este modelo en el [CConnectionPoint](../mfc/reference/cconnectionpoint-class.md) y [CCmdTarget](../mfc/reference/ccmdtarget-class.md) clases. Las clases derivadas de **CConnectionPoint** implementar la **IConnectionPoint** interfaz, que se utiliza para exponer los puntos de conexión a otros objetos. Las clases derivadas de `CCmdTarget` implementar la **IConnectionPointContainer** interfaz, que puede todos los puntos de conexión disponibles de un objeto de enumerar o buscar un punto de conexión concreto.  
  
 Para cada punto de conexión implementado en la clase, se debe declarar un elemento de conexión que implementa el punto de conexión. Si implementa uno o varios puntos de conexión, también debe declarar un mapa de conexión única en la clase. Un mapa de conexión es una tabla de puntos de conexión compatibles con el control ActiveX.  
  
 Los ejemplos siguientes muestran un mapa de conexión simple y un punto de conexión. El primer ejemplo declara el mapa de conexión y el punto; el segundo ejemplo implementa el mapa y el punto. Tenga en cuenta que `CMyClass` debe ser un `CCmdTarget`-clase derivada. En el primer ejemplo de código se inserta en la declaración de clase, en la **protegido** sección:  
  
 [!code-cpp[NVC_MFCConnectionPoints#1](../mfc/codesnippet/cpp/connection-points_1.h)]  
  
 El `BEGIN_CONNECTION_PART` y **END_CONNECTION_PART** macros declaran una clase incrustada, `XSampleConnPt` (derivado de `CConnectionPoint`), que implementa esta conexión concreta del punto. Si desea invalidar cualquier `CConnectionPoint` funciones miembro o agregar funciones miembro de su elección, declárelos entre estas dos macros. Por ejemplo, el `CONNECTION_IID` macro reemplaza el `CConnectionPoint::GetIID` función de miembro al que se encuentra entre estas dos macros.  
  
 En el segundo ejemplo, se inserta código en el archivo de implementación del control (archivo .cpp). Este código implementa el mapa de conexión, que incluye el punto de conexión, `SampleConnPt`:  
  
 [!code-cpp[NVC_MFCConnectionPoints#2](../mfc/codesnippet/cpp/connection-points_2.cpp)]  
  
 Si la clase tiene más de una conexión de punto, inserte adicionales `CONNECTION_PART` macros entre el `BEGIN_CONNECTION_MAP` y `END_CONNECTION_MAP` macros.  
  
 Por último, agregue una llamada a `EnableConnections` en el constructor de clase. Por ejemplo:  
  
 [!code-cpp[NVC_MFCConnectionPoints#3](../mfc/codesnippet/cpp/connection-points_3.cpp)]  
  
 Una vez que se ha insertado este código, su `CCmdTarget`-clase derivada expone un punto de conexión para el **ISampleSink** interfaz. En la siguiente ilustración se muestra en este ejemplo.  
  
 ![Punto de conexión implementado mediante MFC](../mfc/media/vc37lh2.gif "vc37lh2")  
Un punto de conexión implementado con MFC  
  
 Normalmente, los puntos de conexión aceptan "multidifusión": la capacidad para difundir a varios receptores conectados a la misma interfaz. El siguiente fragmento de ejemplo demuestra cómo multidifusión recorriendo en iteración cada receptor en un punto de conexión:  
  
 [!code-cpp[NVC_MFCConnectionPoints#4](../mfc/codesnippet/cpp/connection-points_4.cpp)]  
  
 Este ejemplo recupera el conjunto actual de conexiones en el `SampleConnPt` punto de conexión con una llamada a `CConnectionPoint::GetConnections`. A continuación, recorre las conexiones y las llamadas **ISampleSink:: SinkFunc** en todas las conexiones activas.  
  
## <a name="see-also"></a>Vea también  
 [MFC COM](../mfc/mfc-com.md)

