---
title: "Supporting IDispEventImpl | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDispEventImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL, IDispEventImpl support in COM objects"
  - "BEGIN_SINK_MAP macro"
  - "event sink maps, declarar"
  - "IDispEventImpl class, advising and unadvising"
  - "IDispEventImpl class, declarar"
  - "SINK_ENTRY macro"
  - "bibliotecas de tipos, importar"
ms.assetid: b957f930-6a5b-4598-8e4d-8027759957e7
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Supporting IDispEventImpl
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase de plantilla [IDispEventImpl](../atl/reference/idispeventimpl-class.md) se puede utilizar para proporcionar compatibilidad con los receptores de punto de conexión en la clase ATL.  Un receptor de punto de conexión permite que la clase controle los eventos desencadenados de objetos COM externos.  Asignados a estos receptores de punto de conexión con un mapa de receptor de eventos, proporcionadas por la clase.  
  
 Para implementar correctamente un receptor de punto de conexión para la clase, los siguientes pasos se deben completar:  
  
-   importe las bibliotecas de tipos para cada objeto externo  
  
-   declare las interfaces de `IDispEventImpl`  
  
-   Declare un mapa de receptor de eventos  
  
-   Advise y unadvise los puntos de conexión  
  
 Los pasos necesarios para implementar un receptor todo el punto de conexión son logrados modificando sólo el archivo de encabezado \(.h\) de la clase.  
  
## importar las bibliotecas de tipos  
 Para cada objeto externo cuyos eventos que desea administrar, debe importar la biblioteca de tipos.  Este paso define los eventos que se pueden controlar y proporciona información que se utiliza al declarar el mapa de receptor de eventos.  La directiva de [\#import](../preprocessor/hash-import-directive-cpp.md) se puede utilizar para ello.  Agregue las líneas directivas necesarias de `#import` para cada interfaz de implementación que se admitirá al archivo de encabezado \(.h\) de la clase.  
  
 El ejemplo siguiente importa la biblioteca de tipos desde un servidor COM externo \(`MSCAL.Calendar.7`\):  
  
 [!code-cpp[NVC_ATL_Windowing#141](../atl/codesnippet/CPP/supporting-idispeventimpl_1.h)]  
  
> [!NOTE]
>  Debe tener una instrucción independiente de `#import` para cada biblioteca de tipos externa que se admitirá.  
  
## Declarar interfaces de IDispEventImpl  
 Ahora que ha importado las bibliotecas de tipos de cada interfaz de envío, es necesario declarar interfaces independientes de `IDispEventImpl` para cada interfaz de envío externa.  Modifique la declaración de clase agregando una declaración de interfaz de `IDispEventImpl` para cada objeto externo.  Para obtener más información sobre los parámetros, vea [IDispEventImpl](../atl/reference/idispeventimpl-class.md).  
  
 El código siguiente declara dos receptores de punto de conexión, para la interfaz de `DCalendarEvents` , porque el objeto COM implementado por la clase `CMyCompositCtrl2`:  
  
 [!code-cpp[NVC_ATL_Windowing#142](../atl/codesnippet/CPP/supporting-idispeventimpl_2.h)]  
  
## Declarar un mapa de receptor de eventos  
 Para que las notificaciones de eventos son administradas por la función adecuada, la clase debe distribuir cada evento al controlador correcto.  Esto se logra declarando un mapa de receptor de eventos.  
  
 ATL proporciona varias macros, [BEGIN\_SINK\_MAP](../Topic/BEGIN_SINK_MAP.md), [END\_SINK\_MAP](../Topic/END_SINK_MAP.md), y [SINK\_ENTRY\_EX](../Topic/SINK_ENTRY.md), que crean esta asignación más fácil.  El formato estándar es la siguiente:  
  
 `BEGIN_SINK_MAP(comClass)`  
  
 `SINK_ENTRY_EX(id, iid, dispid, func)`  
  
 `.  .  .  //additional external event entries`  
  
 `END_SINK_MAP()`  
  
 El ejemplo siguiente declara un receptor de eventos asignado con dos controladores de eventos:  
  
 [!code-cpp[NVC_ATL_Windowing#136](../atl/codesnippet/CPP/supporting-idispeventimpl_3.h)]  
  
 la implementación se completa casi.  El último paso se refiere a muestran y a unadvising de interfaces externas.  
  
## El muestran y Unadvising interfaces de IDispEventImpl  
 El paso final es implementar un método que advise \(o unadvise\) todos los puntos de conexión en los tiempos adecuados.  Esto indica que se debe hacer antes de la comunicación entre los clientes externos y el objeto puede tener lugar.  Antes de que el objeto esté visible, cada interfaz de envío externa admitida por el objeto se consulta para las interfaces de salida.  Se establece una conexión y una referencia a la interfaz de salida se usa para controlar eventos de objeto.  Este procedimiento se denomina “aconsejando.”  
  
 Después de que el objeto termina con interfaces externas, las interfaces de salida deben ser notificadas que utiliza ya no por la clase.  Este proceso se conoce como “unadvising.”  
  
 Debido a la naturaleza única de objetos COM, este procedimiento varía, con detalle y ejecución, entre las implementaciones.  Estos detalles están fuera del ámbito de este tema y no se envían.  
  
## Vea también  
 [Fundamentals of ATL COM Objects](../atl/fundamentals-of-atl-com-objects.md)