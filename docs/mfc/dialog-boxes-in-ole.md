---
title: "Cuadros de di&#225;logo en OLE | Microsoft Docs"
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
  - "cuadros de diálogo"
  - "cuadros de diálogo, acerca de los cuadros de diálogo"
  - "cuadros de diálogo, OLE"
  - "insertar objeto"
  - "cuadros de diálogo de MFC, cuadros de diálogo de OLE"
  - "cuadros de diálogo de OLE"
  - "cuadros de diálogo de OLE, acerca de los cuadros de diálogo de OLE"
ms.assetid: 73c41eb8-738a-4d02-9212-d3395bb09a3a
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Cuadros de di&#225;logo en OLE
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Mientras un usuario ejecuta una aplicación OLE\- habilitada, hay ocasiones en que la aplicación necesita información del usuario para realizar la operación.  Las clases VIEJAS MFC proporcionan varios cuadros de diálogo para recopilar la información necesaria.  Este tema muestra las tareas administradas por los cuadros de diálogo de OLE y clases necesarios para mostrar estos cuadros de diálogo.  Para obtener información detallada sobre los cuadros de diálogo de OLE y las estructuras que se utilizan para personalizar su comportamiento, vea [Referencia de MFC](../mfc/mfc-desktop-applications.md).  
  
 *Insertar objeto*  
 Este cuadro de diálogo permite al usuario inserte objetos creados recientemente o existentes en el documento compuesto.  También permite que el usuario elija para mostrar el elemento como un icono y habilita el botón de comando de icono de cambio.  Mostrar este cuadro de diálogo cuando el usuario elige el objeto INSERT en el menú Edición.  Utilice la clase de [COleInsertDialog](../mfc/reference/coleinsertdialog-class.md) para mostrar este cuadro de diálogo.  Observe que no puede incrustar una aplicación MDI en sí mismo.  Una aplicación que es un contenedor\/servidor no se pueden insertar en sí mismo a menos que sea una aplicación SDI.  
  
 *Pegado especial*  
 Este cuadro de diálogo permite al usuario controlar el formato utilizado al pegar datos en un documento compuesto.  El usuario puede elegir el formato de los datos, si insertar o vincular los datos, y si mostrarlo como icono.  Mostrar este cuadro de diálogo cuando el usuario elige el Pegado especial en el menú Edición.  Utilice la clase de [COlePasteSpecialDialog](../mfc/reference/colepastespecialdialog-class.md) para mostrar este cuadro de diálogo.  
  
 *Cambie el icono*  
 Este cuadro de diálogo permite al usuario seleccione el icono aparece para representar el elemento incrustado o vinculado.  Mostrar este cuadro de diálogo cuando el usuario elige el icono de cambio de menú Edición o elija el botón de icono de cambio en los cuadros de diálogo de pegar especial o convert.  También mostrarlo cuando el usuario abre el cuadro de diálogo de objeto INSERT y elija la presentación como icono.  Utilice la clase de [COleChangeIconDialog](../mfc/reference/colechangeicondialog-class.md) para mostrar este cuadro de diálogo.  
  
 *Convertir*  
 Este cuadro de diálogo permite que el usuario cambie el tipo de un elemento incrustado o vinculado.  Por ejemplo, si ha insertado un metarchivo en un documento compuesto y desea después para utilizar otra aplicación para modificar el metarchivo incrustado, puede utilizar el cuadro de diálogo convert.  Este cuadro de diálogo se muestra normalmente haciendo clic en el objeto *del tipo de elemento* en el menú Edición y después, en el menú en cascada, haciendo clic en convertir.  Utilice la clase de [COleConvertDialog](../mfc/reference/coleconvertdialog-class.md) para mostrar este cuadro de diálogo.  Para obtener un ejemplo, ejecute el ejemplo OLE [OCLIENT](../top/visual-cpp-samples.md)MFC.  
  
 *Edite los vínculos o actualizar los vínculos*  
 El cuadro de diálogo de los vínculos de edición permite al usuario a la información de cambio sobre el origen de un objeto vinculado.  El cuadro de diálogo de los vínculos de actualización comprueba los orígenes de todos los elementos vinculados en el cuadro de diálogo actual y muestra el cuadro de diálogo de los vínculos de edición en caso necesario.  Muestre el cuadro de diálogo de los vínculos de edición cuando el usuario elige vínculos en el menú Edición.  El cuadro de diálogo de los vínculos de actualización se muestra normalmente cuando se abre un documento compuesto primero.  Utilice [COleLinksDialog](../mfc/reference/colelinksdialog-class.md) o la clase de [COleUpdateDialog](../mfc/reference/coleupdatedialog-class.md) , dependiendo de cuadro de diálogo que desea mostrar.  
  
 *Servidor ocupado o Servidor No Responder*  
 El cuadro de diálogo No disponible del Servidor se muestra cuando el usuario intenta generar un elemento y el servidor no puede actualmente controlar la solicitud, normalmente porque el servidor está en uso por otro usuario o tarea.  Aparecerá el cuadro de diálogo No Responder de Servidor si el servidor no responde a la solicitud de activación en absoluto.  Estos cuadros de diálogo se muestran mediante `COleMessageFilter`, basándose en una implementación de la interfaz **IMessageFilter**OLE, y el usuario puede decidir si intentar la activación solicita de nuevo.  Utilice la clase de [COleBusyDialog](../mfc/reference/colebusydialog-class.md) para mostrar este cuadro de diálogo.  
  
## Vea también  
 [Cuadros de diálogo](../mfc/dialog-boxes.md)   
 [Ciclo de vida de un cuadro de diálogo](../mfc/life-cycle-of-a-dialog-box.md)   
 [OLE](../mfc/ole-in-mfc.md)