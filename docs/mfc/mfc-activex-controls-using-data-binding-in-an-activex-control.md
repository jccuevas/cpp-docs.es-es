---
title: "Controles ActiveX MFC: Usar el enlace de datos en un control ActiveX | Microsoft Docs"
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
  - "bindable"
  - "requestedit"
  - "defaultbind"
  - "displaybind"
  - "dispid"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "controles enlazados [C++], ActiveX en MFC"
  - "controles [MFC], enlace de datos"
  - "enlace de datos [C++], controles ActiveX en MFC"
  - "controles enlazados a datos [C++], controles ActiveX en MFC"
  - "controles ActiveX en MFC, enlace de datos"
ms.assetid: 476b590a-bf2a-498a-81b7-dd476bd346f1
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Controles ActiveX MFC: Usar el enlace de datos en un control ActiveX
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Uno de los usos más eficaces de controles ActiveX es el enlace de datos, lo que permite que una propiedad de control enlace con un campo concreto en una base de datos.  Cuando un usuario modifica datos en esta propiedad enlazada, el control notifica a la base de datos y las solicitudes que el campo de registro están actualizados.  La base de datos a continuación notifica al control de corrección o error de la solicitud.  
  
 Este artículo trata el lado del control de la tarea.  Implementar las interacciones del enlace de datos con la base de datos es responsabilidad del contenedor del control.  Cómo se administran las interacciones de base de datos en el contenedor está fuera del ámbito de esta documentación.  Cómo se prepara el control para el enlace de datos se explica en el resto de este artículo.  
  
 ![Diagrama conceptual de un control enlazado a datos](../mfc/media/vc374v1.png "vc374V1")  
Diagrama conceptual de un control enlazado a datos  
  
 La clase de `COleControl` proporciona dos funciones miembro que crean enlace de datos un proceso sencillo para implementar.  La primera función, [BoundPropertyRequestEdit](../Topic/COleControl::BoundPropertyRequestEdit.md), se utiliza para solicitar permiso para cambiar el valor de propiedad.  se llama[BoundPropertyChanged](../Topic/COleControl::BoundPropertyChanged.md), la segunda función, después de que el valor de propiedad se ha cambiado correctamente.  
  
 En este artículo se tratan los siguientes temas:  
  
-   [Crear una propiedad común enlazable](#vchowcreatingbindablestockproperty)  
  
-   [Creando un enlazable get\/set el método](#vchowcreatingbindablegetsetmethod)  
  
##  <a name="vchowcreatingbindablestockproperty"></a> Crear una propiedad común enlazable  
 Es posible crear una propiedad de la acción de dato\- límite, aunque es más probable que desee [enlazable get\/set el método](#vchowcreatingbindablegetsetmethod).  
  
> [!NOTE]
>  Las propiedades comunes tienen los atributos de **bindable** y de **requestedit** de forma predeterminada.  
  
#### Para agregar una propiedad común enlazable mediante el asistente para agregar propiedades  
  
1.  Inicia un proyecto mediante [Asistente para controles ActiveX MFC](../mfc/reference/mfc-activex-control-wizard.md).  
  
2.  Haga clic con el botón secundario en el nodo de la interfaz para el control.  
  
     Esto abre el menú contextual.  
  
3.  En el menú contextual, haga clic en **Add** y haga clic en **Agregar propiedad**.  
  
4.  Seleccione una de las entradas de la lista desplegable de **PropertyName** .  Por ejemplo, puede seleccionar **Texto**.  
  
     Dado que **Texto** es una propiedad común, los atributos de **bindable** y de **requestedit** se comprueban ya.  
  
5.  Active las casillas siguientes desde la ficha de **Atributos IDL** : **displaybind** y **defaultbind** para agregar atributos a la definición de propiedad del archivo de .IDL del proyecto.  Estos atributos hacen que el control visible para el usuario y crea la propiedad común la propiedad enlazable predeterminada.  
  
 En este punto, el control puede mostrar datos de un origen de datos, pero el usuario no podrá actualizar los campos de datos.  Si desea que el control también para poder actualizar datos, cambiar la función de `OnOcmCommand`[OnOcmCommand](../mfc/mfc-activex-controls-subclassing-a-windows-control.md) para ser la siguiente:  
  
 [!code-cpp[NVC_MFC_AxData#1](../mfc/codesnippet/CPP/mfc-activex-controls-using-data-binding-in-an-activex-control_1.cpp)]  
  
 Ahora puede compilar el proyecto, que registrará el control.  Cuando se inserta el control en un cuadro de diálogo, las propiedades de **Campo de datos** y de **Origen de datos** se habrán agregado y puede seleccionar un origen de datos y un campo para mostrar en el control.  
  
##  <a name="vchowcreatingbindablegetsetmethod"></a> Creando un enlazable get\/set el método  
 Además de un dato\- límite get\/set el método, también puede crear [propiedad común enlazable](#vchowcreatingbindablestockproperty).  
  
> [!NOTE]
>  Este procedimiento se supone que tiene un proyecto de control ActiveX que cree subclases un control de Windows.  
  
#### Para agregar un enlazable obtenga o establezca el método mediante el asistente para agregar propiedades  
  
1.  Cargue el proyecto de control.  
  
2.  En la página de **Configuración del control** , seleccione una clase de ventana para que el control cree subclases.  Por ejemplo, quizá desee crear subclases de un control de edición.  
  
3.  Cargue el proyecto de control.  
  
4.  Haga clic con el botón secundario en el nodo de la interfaz para el control.  
  
     Esto abre el menú contextual.  
  
5.  En el menú contextual, haga clic en **Add** y haga clic en **Agregar propiedad**.  
  
6.  Escriba el nombre de propiedad en el cuadro de **Nombre de propiedad** .  Utilice `MyProp` para este ejemplo.  
  
7.  Seleccione un tipo de datos de cuadro de lista desplegable de **Tipo de propiedad** .  Uso **corto** para este ejemplo.  
  
8.  Para **Tipo de implementación**, haga clic en **Get\/Set Methods**.  
  
9. Active las casillas siguientes de la pestaña de atributos IDL: **bindable**, **requestedit**, **displaybind**, y **defaultbind** para agregar atributos a la definición de propiedad del archivo de .IDL del proyecto.  Estos atributos hacen que el control visible para el usuario y crea la propiedad común la propiedad enlazable predeterminada.  
  
10. Haga clic en **Finalizar**.  
  
11. Modifique el cuerpo de la función de `SetMyProp` de modo que contenga el código siguiente:  
  
     [!code-cpp[NVC_MFC_AxData#2](../mfc/codesnippet/CPP/mfc-activex-controls-using-data-binding-in-an-activex-control_2.cpp)]  
  
12. El parámetro pasado a las funciones de `BoundPropertyChanged` y de `BoundPropertyRequestEdit` es el dispid de la propiedad, que es el parámetro que se pasa al atributo id. \(\) de la propiedad en el archivo de .IDL.  
  
13. Modifique la función de [OnOcmCommand](../mfc/mfc-activex-controls-subclassing-a-windows-control.md) lo que contiene el código siguiente:  
  
     [!code-cpp[NVC_MFC_AxData#1](../mfc/codesnippet/CPP/mfc-activex-controls-using-data-binding-in-an-activex-control_1.cpp)]  
  
14. Modifique la función de `OnDraw` de modo que contenga el código siguiente:  
  
     [!code-cpp[NVC_MFC_AxData#3](../mfc/codesnippet/CPP/mfc-activex-controls-using-data-binding-in-an-activex-control_3.cpp)]  
  
15. A la sección pública del archivo de encabezado el archivo de encabezado para la clase de control, agrega las definiciones siguientes \(constructores\) para las variables miembro:  
  
     [!code-cpp[NVC_MFC_AxData#4](../mfc/codesnippet/CPP/mfc-activex-controls-using-data-binding-in-an-activex-control_4.h)]  
  
16. Haga que la siguiente línea la última línea en `DoPropExchange` funciona:  
  
     [!code-cpp[NVC_MFC_AxData#5](../mfc/codesnippet/CPP/mfc-activex-controls-using-data-binding-in-an-activex-control_5.cpp)]  
  
17. Modifique la función de `OnResetState` de modo que contenga el código siguiente:  
  
     [!code-cpp[NVC_MFC_AxData#6](../mfc/codesnippet/CPP/mfc-activex-controls-using-data-binding-in-an-activex-control_6.cpp)]  
  
18. Modifique la función de `GetMyProp` de modo que contenga el código siguiente:  
  
     [!code-cpp[NVC_MFC_AxData#7](../mfc/codesnippet/CPP/mfc-activex-controls-using-data-binding-in-an-activex-control_7.cpp)]  
  
 Ahora puede compilar el proyecto, que registrará el control.  Cuando se inserta el control en un cuadro de diálogo, las propiedades de **Campo de datos** y de **Origen de datos** se habrán agregado y puede seleccionar un origen de datos y un campo para mostrar en el control.  
  
## Vea también  
 [Controles ActiveX MFC](../mfc/mfc-activex-controls.md)   
 [Controles enlazados a datos \(ADO y RDO\)](../data/ado-rdo/data-bound-controls-ado-and-rdo.md)