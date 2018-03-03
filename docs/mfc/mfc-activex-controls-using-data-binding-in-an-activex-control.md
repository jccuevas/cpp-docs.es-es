---
title: 'Controles ActiveX MFC: Utilizar enlace de datos en un Control ActiveX | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- bindable
- requestedit
- defaultbind
- displaybind
- dispid
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], data binding
- data binding [MFC], MFC ActiveX controls
- data-bound controls [MFC], MFC ActiveX controls
- controls [MFC], data binding
- bound controls [MFC], MFC ActiveX
ms.assetid: 476b590a-bf2a-498a-81b7-dd476bd346f1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 691f832717f5a71c461316b725ee9a69d1350124
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-activex-controls-using-data-binding-in-an-activex-control"></a>Controles ActiveX de MFC: utilizar enlace de datos en un control ActiveX
Uno de los usos más eficaces de controles ActiveX es el enlace de datos, lo que permite una propiedad del control para enlazar con un campo específico de una base de datos. Cuando un usuario modifica los datos en la propiedad enlazada, el control notifica a la base de datos y las solicitudes que se actualiza el campo de registro. La base de datos, a continuación, notifica el control del éxito o error de la solicitud.  
  
 Este artículo trata del lado del control de la tarea. La implementación de las interacciones de enlace de datos con la base de datos es responsabilidad del contenedor del control. Cómo administrar las interacciones de la base de datos en el contenedor queda fuera del ámbito de esta documentación. En el resto de este artículo se explica cómo preparar el control para el enlace de datos.  
  
 ![Diagrama conceptual de datos &#45; control enlazado](../mfc/media/vc374v1.gif "vc374v1")  
Diagrama conceptual de un Control enlazado a datos  
  
 La `COleControl` clase proporciona dos funciones miembro que hacen que un proceso sencillo para implementar de enlace de datos. La primera función [BoundPropertyRequestEdit](../mfc/reference/colecontrol-class.md#boundpropertyrequestedit), se utiliza para solicitar permiso para cambiar el valor de propiedad. [BoundPropertyChanged](../mfc/reference/colecontrol-class.md#boundpropertychanged), la segunda función, se llama después de que el valor de propiedad se haya cambiado correctamente.  
  
 En este artículo se tratan los siguientes temas:  
  
-   [Crear una propiedad estándar enlazable](#vchowcreatingbindablestockproperty)  
  
-   [Crear un método Get/Set enlazable](#vchowcreatingbindablegetsetmethod)  
  
##  <a name="vchowcreatingbindablestockproperty"></a>Crear una propiedad estándar enlazable  
 Es posible crear una propiedad estándar enlazada a datos, aunque es más probable que desee un [método get/set enlazable](#vchowcreatingbindablegetsetmethod).  
  
> [!NOTE]
>  Las propiedades estándar tienen la **enlazables** y **requestedit** atributos de forma predeterminada.  
  
#### <a name="to-add-a-bindable-stock-property-using-the-add-property-wizard"></a>Para agregar una propiedad estándar enlazable mediante el Asistente para agregar propiedades  
  
1.  Empezar un proyecto mediante el [Asistente para controles ActiveX de MFC](../mfc/reference/mfc-activex-control-wizard.md).  
  
2.  Haga clic en el nodo de interfaz para el control.  
  
     Se abrirá el menú contextual.  
  
3.  En el menú contextual, haga clic en **agregar** y, a continuación, haga clic en **Agregar propiedad**.  
  
4.  Seleccione una de las entradas de la **nombre de la propiedad** lista desplegable. Por ejemplo, puede seleccionar **texto**.  
  
     Dado que **texto** es una propiedad estándar, el **enlazables** y **requestedit** atributos ya están seleccionados.  
  
5.  Active las casillas de verificación siguientes de la **atributos IDL** ficha: **displaybind** y **defaultbind** para agregar los atributos a la definición de propiedad en el proyecto. Este archivo IDL. Estos atributos del control es visible para el usuario y llevar a cabo la propiedad estándar la propiedad enlazable predeterminada.  
  
 En este punto, el control puede mostrar datos de un origen de datos, pero el usuario no podrá actualizar los campos de datos. Si desea que el control también pueda actualizar datos, cambie la `OnOcmCommand` [OnOcmCommand](../mfc/mfc-activex-controls-subclassing-a-windows-control.md) función a tener el aspecto siguiente:  
  
 [!code-cpp[NVC_MFC_AxData#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_1.cpp)]  
  
 Ahora puede compilar el proyecto, que se registrará el control. Al insertar el control en un cuadro de diálogo, el **campo de datos** y **origen de datos** propiedades se habrán agregadas y ahora puede seleccionar un origen de datos y un campo que se muestra en el control.  
  
##  <a name="vchowcreatingbindablegetsetmethod"></a>Crear un método Get/Set enlazable  
 Además de un enlace de datos método get/set, también puede crear un [propiedad estándar enlazable](#vchowcreatingbindablestockproperty).  
  
> [!NOTE]
>  Este procedimiento se da por supuesto que tiene un control ActiveX proyecto que cree subclases de un control de Windows.  
  
#### <a name="to-add-a-bindable-getset-method-using-the-add-property-wizard"></a>Para agregar un método get/set enlazable mediante el Asistente para agregar propiedades  
  
1.  Cargue el proyecto del control.  
  
2.  En el **configuración del Control** , seleccione una clase de ventana para el control para crear una subclase. Por ejemplo, puede que desee para crear subclases de un control de edición.  
  
3.  Cargue el proyecto del control.  
  
4.  Haga clic en el nodo de interfaz para el control.  
  
     Se abrirá el menú contextual.  
  
5.  En el menú contextual, haga clic en **agregar** y, a continuación, haga clic en **Agregar propiedad**.  
  
6.  Escriba el nombre de propiedad en el **nombre de la propiedad** cuadro. Use `MyProp` para este ejemplo.  
  
7.  Seleccione un tipo de datos en el **tipo de propiedad** cuadro de lista desplegable. Use **breve** en este ejemplo.  
  
8.  Para **Tipo de implementación**, haga clic en **Métodos Get/Set**.  
  
9. Seleccione las casillas de verificación siguientes en la ficha atributos IDL: **enlazables**, **requestedit**, **displaybind**, y **defaultbind** para agregar los atributos a la definición de propiedad en el proyecto. Este archivo IDL. Estos atributos del control es visible para el usuario y llevar a cabo la propiedad estándar la propiedad enlazable predeterminada.  
  
10. Haga clic en **Finalizar**.  
  
11. Modificar el cuerpo de la `SetMyProp` función para que contenga el código siguiente:  
  
     [!code-cpp[NVC_MFC_AxData#2](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_2.cpp)]  
  
12. El parámetro pasado a la `BoundPropertyChanged` y `BoundPropertyRequestEdit` funciones es el identificador dispid de la propiedad, que es el parámetro pasado al atributo ID de la propiedad en el. Este archivo IDL.  
  
13. Modificar el [OnOcmCommand](../mfc/mfc-activex-controls-subclassing-a-windows-control.md) funcionan por lo que contiene el código siguiente:  
  
     [!code-cpp[NVC_MFC_AxData#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_1.cpp)]  
  
14. Modificar el `OnDraw` función para que contenga el código siguiente:  
  
     [!code-cpp[NVC_MFC_AxData#3](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_3.cpp)]  
  
15. En la sección pública del archivo de encabezado del archivo de encabezado para la clase del control, agregue las siguientes definiciones (constructores) para variables de miembro:  
  
     [!code-cpp[NVC_MFC_AxData#4](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_4.h)]  
  
16. Realice la siguiente línea de la última línea en el `DoPropExchange` función:  
  
     [!code-cpp[NVC_MFC_AxData#5](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_5.cpp)]  
  
17. Modificar el `OnResetState` función para que contenga el código siguiente:  
  
     [!code-cpp[NVC_MFC_AxData#6](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_6.cpp)]  
  
18. Modificar el `GetMyProp` función para que contenga el código siguiente:  
  
     [!code-cpp[NVC_MFC_AxData#7](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_7.cpp)]  
  
 Ahora puede compilar el proyecto, que se registrará el control. Al insertar el control en un cuadro de diálogo, el **campo de datos** y **origen de datos** propiedades se habrán agregadas y ahora puede seleccionar un origen de datos y un campo que se muestra en el control.  
  
## <a name="see-also"></a>Vea también  
 [Controles ActiveX MFC](../mfc/mfc-activex-controls.md)   

