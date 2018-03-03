---
title: "Cuadros de diálogo en OLE | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- MFC dialog boxes [MFC], OLE dialog boxes
- OLE dialog boxes
- dialog boxes
- OLE dialog boxes [MFC], about OLE dialog boxes
- dialog boxes [MFC], about dialog boxes
- dialog boxes [MFC], OLE
- Insert object
ms.assetid: 73c41eb8-738a-4d02-9212-d3395bb09a3a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 96dfe1828ae3451411adf3ab57c1ec67db24c34e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="dialog-boxes-in-ole"></a>Cuadros de diálogo en OLE
Mientras un usuario ejecuta una aplicación habilitada para OLE, hay ocasiones cuando la aplicación necesita información del usuario con el fin de realizar la operación. Las clases OLE de MFC proporcionan una serie de cuadros de diálogo para recopilar la información necesaria. Este tema enumeran las tareas que se controlan mediante los cuadros de diálogo OLE y las clases necesarias para mostrar los cuadros de diálogo. Para obtener más información sobre los cuadros de diálogo OLE y las estructuras que se usa para personalizar su comportamiento, vea [referencia de MFC](../mfc/mfc-desktop-applications.md).  
  
 *Insertar objeto*  
 Este cuadro de diálogo permite al usuario insertar objetos existentes o recién creados en el documento compuesto. También permite al usuario elegir si desea mostrar el elemento como un icono y habilita el botón de comando Cambiar icono. Mostrar este cuadro de diálogo cuando el usuario selecciona Insertar objeto en el menú Edición. Use la [clase COleInsertDialog](../mfc/reference/coleinsertdialog-class.md) clase para mostrar este cuadro de diálogo. Tenga en cuenta que no se puede insertar una aplicación MDI en sí mismo. Una aplicación que es un contenedor/servidor no se pueden insertar en sí mismo a menos que sea una aplicación SDI.  
  
 *Pegado especial*  
 Este cuadro de diálogo permite al usuario controlar el formato que se utiliza cuando se pegan datos en un documento compuesto. El usuario puede elegir el formato de los datos, si se debe incrustar o vincular los datos y si debe mostrarse como un icono. Mostrar este cuadro de diálogo cuando el usuario elige Pegado especial en el menú Edición. Use la [clase COlePasteSpecialDialog](../mfc/reference/colepastespecialdialog-class.md) clase para mostrar este cuadro de diálogo.  
  
 *Cambiar icono*  
 Este cuadro de diálogo permite al usuario seleccionar qué icono se muestra para representar el elemento vinculado o incrustado. Mostrar este cuadro de diálogo cuando el usuario elige el icono de cambio en el menú Edición o elige el botón Cambiar icono de pegado especial o cuadros de diálogo de Convert. Hacer que aparezca cuando el usuario abre el cuadro de diálogo Insertar objeto y seleccione Mostrar como icono. Use la [clase COleChangeIconDialog](../mfc/reference/colechangeicondialog-class.md) clase para mostrar este cuadro de diálogo.  
  
 *Convertir*  
 Este cuadro de diálogo permite al usuario cambiar el tipo de un elemento vinculado o incrustado. Por ejemplo, si tiene incrustado un metarchivo en un documento compuesto y posteriormente desea volver a utilizar otra aplicación para modificar el metarchivo incrustado, puede usar el cuadro de diálogo convertir. Normalmente se muestra este cuadro de diálogo, haga clic en *tipo de elemento* objeto en el menú Editar y, a continuación, en el menú en cascada, haciendo clic en convertir. Use la [clase COleConvertDialog](../mfc/reference/coleconvertdialog-class.md) clase para mostrar este cuadro de diálogo. Para obtener un ejemplo, ejecutar el ejemplo de MFC OLE [OCLIENT](../visual-cpp-samples.md).  
  
 *Vínculos de edición o actualice los vínculos*  
 El cuadro de diálogo Editar vínculos permite al usuario cambiar la información sobre el origen de un objeto vinculado. El cuadro de diálogo Actualizar vínculos verifica los orígenes de todos los elementos vinculados en el cuadro de diálogo actual y muestra el cuadro de diálogo Editar vínculos si es necesario. Mostrar el cuadro de diálogo Editar vínculos cuando el usuario elige vínculos en el menú Edición. El cuadro de diálogo vínculos de actualización se muestra normalmente cuando se abre un documento compuesto por primera vez. Utilice la [COleLinksDialog](../mfc/reference/colelinksdialog-class.md) o [COleUpdateDialog](../mfc/reference/coleupdatedialog-class.md) de clases, dependiendo de qué cuadro de diálogo que desea mostrar.  
  
 *Servidor ocupado o no responde*  
 Cuando el usuario intenta activar un elemento y el servidor está actualmente no se puede atender la solicitud, normalmente porque el servidor está en uso por otro usuario o tarea, se muestra el cuadro de diálogo servidor ocupado. Si el servidor no responde en absoluto a la solicitud de activación, se muestra el cuadro de diálogo servidor no responde. Estos cuadros de diálogo se muestran a través de `COleMessageFilter`, en función de una implementación de la interfaz OLE **IMessageFilter**, y el usuario puede decidir si desea que se vuelva a intentar la solicitud de activación. Use la [clase COleBusyDialog](../mfc/reference/colebusydialog-class.md) clase para mostrar este cuadro de diálogo.  
  
## <a name="see-also"></a>Vea también  
 [Cuadros de diálogo](../mfc/dialog-boxes.md)   
 [Ciclo de vida de un cuadro de diálogo](../mfc/life-cycle-of-a-dialog-box.md)   
 [OLE](../mfc/ole-in-mfc.md)

