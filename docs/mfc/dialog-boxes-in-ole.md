---
title: Cuadros de diálogo en OLE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eaa361a75843fb9f99e3378763a62cfaeeeb07c2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46383628"
---
# <a name="dialog-boxes-in-ole"></a>Cuadros de diálogo en OLE

Mientras que un usuario ejecuta una aplicación habilitada para OLE, hay veces cuando la aplicación necesita información del usuario para llevar a cabo la operación. Las clases OLE de MFC proporcionan una serie de cuadros de diálogo para recopilar la información necesaria. En este tema se enumera las tareas que se controlan mediante los cuadros de diálogo OLE y las clases necesarias para mostrar estos cuadros de diálogo. Para obtener más información sobre los cuadros de diálogo OLE y las estructuras que se usa para personalizar su comportamiento, vea [referencia de MFC](../mfc/mfc-desktop-applications.md).

*Insertar objeto*<br/>
Este cuadro de diálogo permite al usuario insertar objetos existentes o recién creados en el documento compuesto. También permite al usuario elegir mostrar el elemento como un icono y habilita el botón de comando Cambiar icono. Mostrar este cuadro de diálogo cuando el usuario elige Insertar objeto en el menú Edición. Use la [COleInsertDialog](../mfc/reference/coleinsertdialog-class.md) clase para mostrar este cuadro de diálogo. Tenga en cuenta que no se puede insertar una aplicación MDI en sí mismo. Una aplicación que es un contenedor y el servidor no puede insertarse en sí mismo a menos que sea una aplicación SDI.

*Pegado especial*<br/>
Este cuadro de diálogo permite al usuario controlar el formato utilizado para pegar datos en un documento compuesto. El usuario puede elegir el formato de los datos, si se debe incrustar o vincular los datos y si se mostrará como un icono. Mostrar este cuadro de diálogo cuando el usuario elige Pegado especial en el menú Edición. Use la [COlePasteSpecialDialog](../mfc/reference/colepastespecialdialog-class.md) clase para mostrar este cuadro de diálogo.

*Cambiar icono*<br/>
Este cuadro de diálogo permite al usuario seleccionar qué icono se muestra para representar el elemento vinculado o incrustado. Mostrar este cuadro de diálogo cuando el usuario elige el icono de cambio en el menú Edición o elige el botón Cambiar icono en el pegado especial o cuadros de diálogo de Convert. Hacer que aparezca cuando el usuario abre el cuadro de diálogo Insertar objeto y seleccione Mostrar como icono. Use la [COleChangeIconDialog](../mfc/reference/colechangeicondialog-class.md) clase para mostrar este cuadro de diálogo.

*Convertir*<br/>
Este cuadro de diálogo permite al usuario cambiar el tipo de un elemento incrustado o vinculado. Por ejemplo, si ha incrustado un metarchivo en un documento compuesto y posteriormente desea utilizar otra aplicación para modificar el metarchivo incrustado, puede usar el cuadro de diálogo convertir. Normalmente, se muestra este cuadro de diálogo, haga clic en *tipo de elemento* objeto en el menú Editar y, a continuación, en el menú en cascada, haciendo clic en convertir. Use la [COleConvertDialog](../mfc/reference/coleconvertdialog-class.md) clase para mostrar este cuadro de diálogo. Por ejemplo, ejecutar el ejemplo OLE de MFC [OCLIENT](../visual-cpp-samples.md).

*Editar vínculos o actualizar vínculos*<br/>
El cuadro de diálogo Editar vínculos permite al usuario cambiar la información sobre el origen de un objeto vinculado. El cuadro de diálogo vínculos de actualización comprueba los orígenes de todos los elementos vinculados en el cuadro de diálogo actual y muestra el cuadro de diálogo Editar vínculos si es necesario. Mostrar el cuadro de diálogo Editar vínculos cuando el usuario elige los vínculos en el menú Edición. Normalmente, se muestra el cuadro de diálogo vínculos de actualización cuando se abre un documento compuesto por primera vez. Usar el [COleLinksDialog](../mfc/reference/colelinksdialog-class.md) o [COleUpdateDialog](../mfc/reference/coleupdatedialog-class.md) class, dependiendo de qué cuadro de diálogo que desea mostrar.

*Servidor ocupado o el servidor no responde*<br/>
Cuando el usuario intenta activar un elemento y el servidor está actualmente no se puede atender la solicitud, normalmente porque el servidor está en uso por otro usuario o tarea, se muestra el cuadro de diálogo servidor ocupado. Si el servidor no responde en absoluto a la solicitud de activación, se muestra el cuadro de diálogo servidor no responde. Estos cuadros de diálogo se muestran a través de `COleMessageFilter`, basándose en una implementación de la interfaz OLE `IMessageFilter`, y el usuario puede decidir si desea que se vuelva a intentar la solicitud de activación. Use la [COleBusyDialog](../mfc/reference/colebusydialog-class.md) clase para mostrar este cuadro de diálogo.

## <a name="see-also"></a>Vea también

[Cuadros de diálogo](../mfc/dialog-boxes.md)<br/>
[Ciclo de vida de un cuadro de diálogo](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[OLE](../mfc/ole-in-mfc.md)

