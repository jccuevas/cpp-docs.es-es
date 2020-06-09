---
title: Puntos de conexión
ms.date: 11/19/2018
f1_keywords:
- IConnectionPoint
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
ms.openlocfilehash: 1a8fc4742b8bf686edf75f3b98cc283b9bf9881b
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620723"
---
# <a name="connection-points"></a>Puntos de conexión

En este artículo se explica cómo implementar puntos de conexión (antes conocidos como puntos de conexión OLE) mediante las clases MFC `CCmdTarget` y `CConnectionPoint` .

En el pasado, el modelo de objetos componentes (COM) definía un mecanismo general ( `IUnknown::QueryInterface` *) que permitía a los objetos implementar y exponer la funcionalidad en las interfaces. Sin embargo, no se definió un mecanismo correspondiente que permitía a los objetos exponer su capacidad para llamar a interfaces específicas. Es decir, COM definía cómo se administraban los punteros entrantes a objetos (punteros a las interfaces del objeto), pero no tenía un modelo explícito para interfaces de salida (punteros que el objeto contiene a otras interfaces de objetos). COM tiene ahora un modelo denominado puntos de conexión que admite esta funcionalidad.

Una conexión tiene dos partes: el objeto que llama a la interfaz, denominado origen, y el objeto que implementa la interfaz, denominado receptor. Un punto de conexión es la interfaz expuesta por el origen. Al exponer un punto de conexión, un origen permite que los receptores establezcan conexiones a sí mismo (el origen). A través del mecanismo de punto de conexión (la `IConnectionPoint` interfaz), se pasa un puntero a la interfaz receptora al objeto de origen. Este puntero proporciona el origen con acceso a la implementación del receptor de un conjunto de funciones miembro. Por ejemplo, para desencadenar un evento implementado por el receptor, el origen puede llamar al método adecuado de la implementación del receptor. En la siguiente ilustración se muestra el punto de conexión que se acaba de describir.

![Punto de conexión implementado](../mfc/media/vc37lh1.gif "Punto de conexión implementado") <br/>
Un punto de conexión implementado

MFC implementa este modelo en las clases [CConnectionPoint](reference/cconnectionpoint-class.md) y [CCmdTarget](reference/ccmdtarget-class.md) . Las clases derivadas de `CConnectionPoint` implementan la `IConnectionPoint` interfaz, que se utiliza para exponer los puntos de conexión a otros objetos. Las clases derivadas de `CCmdTarget` implementan la `IConnectionPointContainer` interfaz, que puede enumerar todos los puntos de conexión disponibles de un objeto o buscar un punto de conexión específico.

Para cada punto de conexión implementado en la clase, debe declarar una parte de conexión que implemente el punto de conexión. Si implementa uno o más puntos de conexión, también debe declarar una única asignación de conexión en la clase. Un mapa de conexión es una tabla de puntos de conexión admitidos por el control ActiveX.

En los siguientes ejemplos se muestra un mapa de conexión simple y un punto de conexión. En el primer ejemplo se declara la asignación de conexión y el punto; en el segundo ejemplo se implementan el mapa y el punto. Tenga en cuenta que `CMyClass` debe ser una `CCmdTarget` clase derivada de. En el primer ejemplo, el código se inserta en la declaración de clase, en la sección **protegida** :

[!code-cpp[NVC_MFCConnectionPoints#1](codesnippet/cpp/connection-points_1.h)]

Las macros **BEGIN_CONNECTION_PART** y **END_CONNECTION_PART** declaran una clase incrustada `XSampleConnPt` (derivada de `CConnectionPoint` ) que implementa este punto de conexión concreto. Si desea invalidar cualquier `CConnectionPoint` función miembro o agregar funciones miembro propias, declárela entre estas dos macros. Por ejemplo, la `CONNECTION_IID` macro invalida la `CConnectionPoint::GetIID` función miembro cuando se coloca entre estas dos macros.

En el segundo ejemplo, el código se inserta en el archivo de implementación del control (archivo. cpp). Este código implementa la asignación de conexión, que incluye el punto de conexión `SampleConnPt` :

[!code-cpp[NVC_MFCConnectionPoints#2](codesnippet/cpp/connection-points_2.cpp)]

Si la clase tiene más de un punto de conexión, inserte macros **CONNECTION_PART** adicionales entre las macros **BEGIN_CONNECTION_MAP** y **END_CONNECTION_MAP** .

Por último, agregue una llamada a `EnableConnections` en el constructor de la clase. Por ejemplo:

[!code-cpp[NVC_MFCConnectionPoints#3](codesnippet/cpp/connection-points_3.cpp)]

Una vez que se ha insertado este código, la `CCmdTarget` clase derivada de expone un punto de conexión para la `ISampleSink` interfaz. En la ilustración siguiente se muestra este ejemplo.

![Punto de conexión implementado mediante MFC](../mfc/media/vc37lh2.gif "Punto de conexión implementado mediante MFC") <br/>
Un punto de conexión implementado con MFC

Normalmente, los puntos de conexión admiten la "multidifusión", la capacidad de difundir a varios receptores conectados a la misma interfaz. En el fragmento de ejemplo siguiente se muestra cómo se realiza la multidifusión recorriendo cada receptor en un punto de conexión:

[!code-cpp[NVC_MFCConnectionPoints#4](codesnippet/cpp/connection-points_4.cpp)]

En este ejemplo se recupera el conjunto actual de conexiones en el `SampleConnPt` punto de conexión con una llamada a `CConnectionPoint::GetConnections` . A continuación, recorre en iteración las conexiones y llama a `ISampleSink::SinkFunc` en cada conexión activa.

## <a name="see-also"></a>Consulte también

[MFC COM](mfc-com.md)
