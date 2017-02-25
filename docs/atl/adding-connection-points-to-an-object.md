---
title: "Adding Connection Points to an Object | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "puntos de conexión [C++], agregar a objetos ATL"
  - "Implement Connection Point ATL wizard"
ms.assetid: 843531be-4a36-4db0-9d54-e029b1a72a8b
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Adding Connection Points to an Object
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[tutorial de ATL](../atl/active-template-library-atl-tutorial.md) muestra cómo crear un control con compatibilidad para puntos de conexión, cómo agregar eventos, y a continuación cómo implementar el punto de conexión.  ATL implementa los puntos de conexión con la clase de [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) .  
  
 Para implementar un punto de conexión, tiene dos opciones:  
  
-   Implemente poseen origen de eventos de salida, agregando un punto de conexión al control o el objeto.  
  
-   Reutilizar una interfaz de punto de conexión definido en otra biblioteca de tipos.  
  
 En cualquier caso, el asistente para implementar utiliza una biblioteca de tipos para realizar su trabajo.  
  
### Para agregar un punto de conexión a un control o un objeto  
  
1.  Defina una dispinterface en el bloque de la biblioteca del archivo .idl.  Si habilitó la compatibilidad para los puntos de conexión cuando creó el control con el asistente para controles ATL, el dispinterface se creado.  Si no habilitó la compatibilidad para los puntos de conexión cuando creó el control, debe agregar manualmente dispinterface al archivo .idl.  A continuación se muestra un ejemplo de dispinterface.  Las interfaces de salida no necesitan ser interfaces de implementación pero muchos lenguajes de script como VBScript y JScript requieren esto, por lo que este ejemplo utiliza dos dispinterface:  
  
     [!code-cpp[NVC_ATL_Windowing#81](../atl/codesnippet/CPP/adding-connection-points-to-an-object_1.idl)]  
  
     Utilice el uuidgen.exe o la utilidad de guidgen.exe para generar un GUID.  
  
2.  Agregue el dispinterface como interfaz de `[default,source]` en la coclase para el objeto en el archivo .idl del proyecto.  Una vez más si habilitó la compatibilidad para los puntos de conexión cuando creó el control, el asistente para controles ATL creará la entrada de `[default,source`\].  para agregar manualmente esta entrada, agregue la línea en negrita:  
  
     [!code-cpp[NVC_ATL_Windowing#82](../atl/codesnippet/CPP/adding-connection-points-to-an-object_2.idl)]  
  
     Vea el archivo .idl del ejemplo de [Circ](../top/visual-cpp-samples.md) ATL para un ejemplo.  
  
3.  Vista de clases de uso para agregar métodos y propiedades a la interfaz de eventos.  Haga clic con el botón secundario en la clase en la vista de clases, elija **Agregar** en el menú contextual, haga clic en **Agregar Punto de conexión**.  
  
4.  En el cuadro de lista de **Interfaces de origen** del asistente para implementar, seleccione **Las interfaces del proyecto**.  Si elige una interfaz para el control y presione **Aceptar**, debe:  
  
    -   Genere un archivo de encabezado con una clase de proxy del evento que se aplica el código que hará las llamadas salientes para el evento.  
  
    -   Agregue una entrada al mapa de puntos de conexión.  
  
     También verá una lista de todas las bibliotecas de tipos en el equipo.  Debe utilizar sólo una de estas otras bibliotecas de tipos para definir el punto de conexión si desea implementar exactamente la misma interfaz de salida encontrada en otra biblioteca de tipos.  
  
### Reutilizar una interfaz de punto de conexión definido en otra biblioteca de tipos  
  
1.  En la vista de clases, haga clic con el botón secundario en una clase que implemente una macro de **BEGIN\_COM\_MAP** , elija **Agregar** en el menú contextual, haga clic en **Agregar Punto de conexión**.  
  
2.  En el asistente para implementar, seleccione una biblioteca de tipos y una interfaz en la biblioteca de tipos y haga clic **Agregar**.  
  
3.  Edite el archivo .idl cualquiera:  
  
    -   Copie el dispinterface del archivo .idl del objeto cuyo se utiliza origen de eventos.  
  
    -   Utilice la instrucción de **importlib** en la biblioteca de tipos.  
  
## Vea también  
 [Puntos de conexión](../atl/atl-connection-points.md)