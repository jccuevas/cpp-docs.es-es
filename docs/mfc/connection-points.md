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
ms.openlocfilehash: bf21e7bf591a5b1977784db1542053817a73e6cd
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2018
ms.locfileid: "52175488"
---
# <a name="connection-points"></a>Puntos de conexión

En este artículo se explica cómo implementar puntos de conexión (conocidos anteriormente como puntos de conexión OLE) mediante las clases MFC `CCmdTarget` y `CConnectionPoint`.

En el pasado, el modelo de objetos componentes (COM) define un mecanismo general (`IUnknown::QueryInterface`*) que permitía a los objetos implementar y exponer la funcionalidad de las interfaces. Sin embargo, no se definió un mecanismo correspondiente que se permite objetos que se va a exponer su capacidad para llamar a interfaces específicas. Es decir, COM define entrantes punteros a objetos se controlaron (punteros a las interfaces del objeto), pero no tenía un modelo explícito de interfaces de salida (punteros que contiene el objeto a interfaces de otros objetos). Ahora, COM tiene un modelo, denominado puntos de conexión, que es compatible con esta funcionalidad.

Una conexión tiene dos partes: el objeto que llama a la interfaz, denominada el origen y el objeto que implementa la interfaz, llama al receptor. Un punto de conexión es la interfaz expuesta por el origen. Al exponer un punto de conexión, un origen permite a los receptores establecer conexiones a sí mismo (origen). A través de la conexión de punto mecanismo (el `IConnectionPoint` interfaz), se pasa un puntero a la interfaz de receptor para el objeto de origen. This (puntero) proporciona el origen con acceso a la implementación del receptor de un conjunto de funciones miembro. Por ejemplo, para desencadenar un evento implementado por el receptor, el origen puede llamar al método correspondiente de la implementación del receptor. En la siguiente ilustración se muestra la conexión de punto que acabamos de describir.

![Implementa el punto de conexión](../mfc/media/vc37lh1.gif "implementa el punto de conexión") <br/>
Un punto de conexión implementado

MFC implementa este modelo en el [CConnectionPoint](../mfc/reference/cconnectionpoint-class.md) y [CCmdTarget](../mfc/reference/ccmdtarget-class.md) clases. Las clases derivadas de `CConnectionPoint` implementar el `IConnectionPoint` interfaz, se utiliza para exponer los puntos de conexión a otros objetos. Las clases derivadas de `CCmdTarget` implementar el `IConnectionPointContainer` interfaz, que puede enumerar todos los puntos de conexión disponibles de un objeto o buscar un punto de conexión concreto.

Para cada punto de conexión implementado en la clase, debe declarar un elemento de conexión que implementa el punto de conexión. Si implementa uno o varios puntos de conexión, también debe declarar un mapa de conexión único en la clase. Un mapa de la conexión es una tabla de puntos de conexión compatibles con el control ActiveX.

Los ejemplos siguientes muestran un mapa de conexión simple y un punto de conexión. El primer ejemplo declara el mapa de conexión y el punto; el segundo ejemplo implementa el mapa y el punto. Tenga en cuenta que `CMyClass` debe ser un `CCmdTarget`-clase derivada. En el primer ejemplo, se inserta código en la declaración de clase en el **protegido** sección:

[!code-cpp[NVC_MFCConnectionPoints#1](../mfc/codesnippet/cpp/connection-points_1.h)]

El **macros BEGIN_CONNECTION_PART** y **END_CONNECTION_PART** macros declaran una clase incrustada, `XSampleConnPt` (derivado de `CConnectionPoint`), que hacen referencia implementa esta conexión concreta. Si desea reemplazar cualquier `CConnectionPoint` funciones miembro o agregar funciones miembro de su elección, declárelos entre estas dos macros. Por ejemplo, el `CONNECTION_IID` macro reemplaza el `CConnectionPoint::GetIID` función de miembro al que se encuentra entre estos dos macros.

En el segundo ejemplo, se inserta código en el archivo de implementación del control (archivo .cpp). Este código implementa la asignación de la conexión, que incluye el punto de conexión, `SampleConnPt`:

[!code-cpp[NVC_MFCConnectionPoints#2](../mfc/codesnippet/cpp/connection-points_2.cpp)]

Si la clase tiene más de una conexión de punto, inserte adicionales **CONNECTION_PART** macros entre el **BEGIN_CONNECTION_MAP** y **END_CONNECTION_MAP** macros.

Por último, agregue una llamada a `EnableConnections` en el constructor de clase. Por ejemplo:

[!code-cpp[NVC_MFCConnectionPoints#3](../mfc/codesnippet/cpp/connection-points_3.cpp)]

Una vez insertado este código, su `CCmdTarget`-clase derivada expone un punto de conexión para el `ISampleSink` interfaz. En la siguiente ilustración se muestra en este ejemplo.

![Punto de conexión implementado mediante MFC](../mfc/media/vc37lh2.gif "punto de conexión implementado mediante MFC") <br/>
Un punto de conexión implementado con MFC

Por lo general, la compatibilidad de puntos de conexión con "multidifusión": la capacidad para difundir a varios receptores conectados a la misma interfaz. El siguiente fragmento de ejemplo muestra cómo multidifusión recorriendo en iteración cada receptor en un punto de conexión:

[!code-cpp[NVC_MFCConnectionPoints#4](../mfc/codesnippet/cpp/connection-points_4.cpp)]

En este ejemplo recupera el conjunto actual de conexiones en el `SampleConnPt` punto de conexión con una llamada a `CConnectionPoint::GetConnections`. A continuación, recorre en iteración las conexiones y las llamadas `ISampleSink::SinkFunc` en todas las conexiones activas.

## <a name="see-also"></a>Vea también

[MFC COM](../mfc/mfc-com.md)

