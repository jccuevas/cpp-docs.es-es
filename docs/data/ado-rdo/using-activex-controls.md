---
title: "Utilizar controles ActiveX | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "controles ActiveX [C++], acerca de los controles ActiveX"
  - "controles [C++], ActiveX"
ms.assetid: 33442173-205d-492f-82c8-9a8105358ec6
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Utilizar controles ActiveX
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

En los temas de esta sección se ofrece información general sobre el uso de los controles ActiveX.  
  
 Un control ActiveX es un componente COM compatible con interfaces estándar relacionadas con la persistencia, los puntos de conexión y el hospedaje de controles.  Estas interfaces estándar definen un protocolo que permite hospedar un control en un contenedor de controles, intercambiar mensajes y controlar eventos.  
  
 De la misma manera que los servidores COM, los controles ActiveX tienen lo siguiente.  
  
|Término|Descripción|  
|-------------|-----------------|  
|Propiedades|Los controles tienen variables miembro para representar el estado interno y se implementan como funciones para descriptores de acceso **Get** y `Set`.  Se genera una función **Get** para cada método de descriptor de acceso con una etiqueta propget en el archivo .idl.  Se genera una función `Set` para cada método de descriptor de acceso con una etiqueta IDL propput o propputref.<br /><br /> Utilice [clases contenedoras](../../data/ado-rdo/wrapper-classes.md) o el [Visor de objetos OLE y COM](../../data/ado-rdo/using-the-ole-com-object-viewer.md) para determinar cómo deben definirse las funciones para descriptores de acceso.|  
|Métodos|El comportamiento de un control se define mediante sus métodos públicos.  Las clases contenedoras proporcionan acceso a los métodos del control.<br /><br /> Si no se utilizan clases contenedoras \(la opción predeterminada\), se deberá obtener acceso a los métodos de un control mediante la obtención de un puntero a una interfaz.<br /><br /> Un ejemplo de método público es el método **Refresh** en ADO Data Control, que actualiza el conjunto de filas obtenido.|  
|Eventos|Un control puede generar un evento para notificar al host que sucedió algo.  Un ejemplo es el evento `OnClick` para el control Button.  Cuando se hace clic en el botón, éste genera un evento `OnClick`.  Si el host del control tiene un controlador para el evento, se ejecuta dicho controlador.|  
|Biblioteca de tipos|Una biblioteca de tipos indica a un contenedor de control qué propiedades, métodos y eventos admite un control.  Las bibliotecas de tipos pueden existir como archivos independientes \(con una extensión .tlb\) o internamente, dentro del control.<br /><br /> Las bibliotecas de tipos también pueden contener la información de coclase del control.  Una coclase es una clase COM que se identifica mediante un GUID.  Este tipo de clase contiene una o varias interfaces definidas por el control.<br /><br /> Para examinar bibliotecas de tipos, utilice el [Visor de objetos OLE y COM](../../data/ado-rdo/using-the-ole-com-object-viewer.md).|  
  
 En los siguientes temas se describe el uso de un control ActiveX:  
  
-   [Insertar el control en una aplicación de Visual C\+\+](../../data/ado-rdo/inserting-the-control-into-a-visual-cpp-application.md)  
  
-   [Clases contenedoras](../../data/ado-rdo/wrapper-classes.md)  
  
-   [Crear una conexión de base de datos](../../data/ado-rdo/creating-database-connections.md)  
  
-   [Establecer las propiedades de un control en tiempo de diseño](../../data/ado-rdo/setting-control-properties-at-design-time.md)  
  
-   [Establecer controladores de eventos en controles ActiveX](../../data/ado-rdo/setting-event-handlers-on-activex-controls.md)  
  
-   [Modificar el comportamiento de un control en tiempo de ejecución](../../data/ado-rdo/modifying-a-control-s-run-time-behavior.md)  
  
-   [Redistribuir controles](../../data/ado-rdo/redistributing-controls.md)  
  
## Vea también  
 [Controles enlazados a datos \(ADO y RDO\)](../../data/ado-rdo/data-bound-controls-ado-and-rdo.md)