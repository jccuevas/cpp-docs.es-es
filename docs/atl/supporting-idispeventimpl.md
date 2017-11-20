---
title: Compatibilidad con IDispEventImpl | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDispEventImpl
dev_langs: C++
helpviewer_keywords:
- event sink maps, declaring
- IDispEventImpl class, advising and unadvising
- SINK_ENTRY macro
- type libraries, importing
- ATL, IDispEventImpl support in COM objects
- BEGIN_SINK_MAP macro
- IDispEventImpl class, declaring
ms.assetid: b957f930-6a5b-4598-8e4d-8027759957e7
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 81976652c14693c54980f6e0901f5db5576fbbe8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="supporting-idispeventimpl"></a>Compatibilidad con IDispEventImpl
La clase de plantilla [IDispEventImpl](../atl/reference/idispeventimpl-class.md) puede usarse para proporcionar compatibilidad con receptores de puntos de conexión en una clase ATL. Un receptor de puntos de conexión permite a la clase controlar los eventos desencadenados desde objetos COM externos. Estos receptores de puntos de conexión se asignan a un mapa de receptores de eventos, proporcionado por la clase.  
  
 Para implementar correctamente un receptor de puntos de conexión para la clase, deben completar los pasos siguientes:  
  
-   Importar las bibliotecas de tipos para cada objeto externo  
  
-   Declare el `IDispEventImpl` interfaces  
  
-   Declarar un mapa de receptores de eventos  
  
-   Aconsejar y desaconsejar los puntos de conexión  
  
 Los pasos implicados en la implementación de un receptor de puntos de conexión se realizan mediante la modificación solo el archivo de encabezado (. h) de la clase.  
  
## <a name="importing-the-type-libraries"></a>Importar las bibliotecas de tipos  
 Para cada objeto externo cuyos eventos desee controlar, deberá importar la biblioteca de tipos. Este paso define los eventos que se pueden administrar y proporciona información que se usa cuando se declara el mapa de receptores de eventos. El [#import](../preprocessor/hash-import-directive-cpp.md) directiva puede utilizarse para lograr esto. Agregar las necesarias `#import` líneas de directiva para cada interfaz de envío que se va a admitir en el archivo de encabezado (. h) de la clase.  
  
 El siguiente ejemplo importa la biblioteca de tipos de un servidor COM externo (`MSCAL.Calendar.7`):  
  
 [!code-cpp[NVC_ATL_Windowing#141](../atl/codesnippet/cpp/supporting-idispeventimpl_1.h)]  
  
> [!NOTE]
>  Debe tener otro `#import` instrucción para cada biblioteca de tipos externa que se va a admitir.  
  
## <a name="declaring-the-idispeventimpl-interfaces"></a>Declarar las Interfaces IDispEventImpl  
 Ahora que ha importado las bibliotecas de tipos de cada interfaz de envío, deberá declarar independiente `IDispEventImpl` interfaces para cada interfaz de envío externo. Modifique la declaración de la clase agregando un `IDispEventImpl` declaración para cada objeto externo de interfaz. Para obtener más información sobre los parámetros, vea [IDispEventImpl](../atl/reference/idispeventimpl-class.md).  
  
 El código siguiente declara dos receptores de puntos de conexión para el `DCalendarEvents` interfaz para el objeto COM implementado clase `CMyCompositCtrl2`:  
  
 [!code-cpp[NVC_ATL_Windowing#142](../atl/codesnippet/cpp/supporting-idispeventimpl_2.h)]  
  
## <a name="declaring-an-event-sink-map"></a>Declarar un mapa de receptores de eventos  
 Para las notificaciones de eventos ser controladas por la función adecuada, la clase deberá encaminar cada evento a su controlador correcto. Esto se logra mediante la declaración de un mapa de receptores de eventos.  
  
 ATL proporciona varias macros, [BEGIN_SINK_MAP](reference/composite-control-macros.md#begin_sink_map), [END_SINK_MAP](reference/composite-control-macros.md#end_sink_map), y [SINK_ENTRY_EX](reference/composite-control-macros.md#sink_entry_ex), que facilitan estas asignaciones. El formato estándar es como sigue:  
  
 `BEGIN_SINK_MAP(comClass)`  
  
 `SINK_ENTRY_EX(id, iid, dispid, func)`  
  
 `. . . //additional external event entries`  
  
 `END_SINK_MAP()`  
  
 En el ejemplo siguiente se declara un mapa de receptores de eventos con dos controladores de eventos:  
  
 [!code-cpp[NVC_ATL_Windowing#136](../atl/codesnippet/cpp/supporting-idispeventimpl_3.h)]  
  
 La implementación está casi completa. El último paso se refiere a la acción de aconsejar y desaconsejar las interfaces externas.  
  
## <a name="advising-and-unadvising-the-idispeventimpl-interfaces"></a>Aconsejar y desaconsejar las Interfaces IDispEventImpl  
 El paso final consiste en implementar un método que aparezca un mensaje indicando (o no notificar) todos los puntos de conexión en los momentos adecuados. Estos consejos deben realizarse antes de que puede realizar la comunicación entre los clientes externos y el objeto. Antes de que el objeto sea visible, cada interfaz de envío externo compatible con el objeto se consulta para interfaces de salida. Se establece una conexión y una referencia a la interfaz de salida se usa para controlar los eventos del objeto. Este procedimiento se conoce como "aconsejar".  
  
 Cuando finalice el objeto con las interfaces externas, deben notificar las interfaces de salida que ya no se usan por la clase. Este proceso se conoce como "desaconsejar".  
  
 Dada la naturaleza única de los objetos COM, este procedimiento puede variar, en detalle y ejecución, entre las implementaciones. Estos detalles quedan fuera del ámbito de este tema y no se tratan.  
  
## <a name="see-also"></a>Vea también  
 [Aspectos básicos de los objetos ATL COM](../atl/fundamentals-of-atl-com-objects.md)

