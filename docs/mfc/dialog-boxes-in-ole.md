---
title: Cuadros de diálogo en OLE
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], OLE dialog boxes
- OLE dialog boxes
- dialog boxes
- OLE dialog boxes [MFC], about OLE dialog boxes
- dialog boxes [MFC], about dialog boxes
- dialog boxes [MFC], OLE
- Insert object
ms.assetid: 73c41eb8-738a-4d02-9212-d3395bb09a3a
ms.openlocfilehash: 997bfc0bda05f5a2520c102cb38777b533bcef95
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685774"
---
# <a name="dialog-boxes-in-ole"></a>Cuadros de diálogo en OLE

Cuando un usuario ejecuta una aplicación habilitada para OLE, hay ocasiones en las que la aplicación necesita información del usuario para llevar a cabo la operación. Las clases OLE de MFC proporcionan una serie de cuadros de diálogo para recopilar la información necesaria. En este tema se enumeran las tareas controladas por los cuadros de diálogo OLE y las clases necesarias para mostrar los cuadros de diálogo. Para obtener más información sobre los cuadros de diálogo OLE y las estructuras utilizadas para personalizar su comportamiento, vea [referencia de MFC](../mfc/mfc-desktop-applications.md).

*Insertar objeto*<br/>
Este cuadro de diálogo permite al usuario insertar objetos recién creados o existentes en el documento compuesto. También permite al usuario elegir mostrar el elemento como un icono y habilitar el botón de comando Cambiar icono. Mostrar este cuadro de diálogo cuando el usuario elija Insertar objeto en el menú edición. Use la clase [COleInsertDialog](../mfc/reference/coleinsertdialog-class.md) para mostrar este cuadro de diálogo. Tenga en cuenta que no puede insertar una aplicación MDI en sí misma. Una aplicación que es un contenedor o servidor no se puede insertar en sí misma a menos que sea una aplicación SDI.

*Pegado especial*<br/>
Este cuadro de diálogo permite al usuario controlar el formato utilizado al pegar datos en un documento compuesto. El usuario puede elegir el formato de los datos, si se van a incrustar o vincular los datos, y si se va a mostrar como un icono. Mostrar este cuadro de diálogo cuando el usuario elija Pegar especial en el menú edición. Use la clase [COlePasteSpecialDialog](../mfc/reference/colepastespecialdialog-class.md) para mostrar este cuadro de diálogo.

*Cambiar icono*<br/>
Este cuadro de diálogo permite al usuario seleccionar el icono que se muestra para representar el elemento vinculado o incrustado. Muestra este cuadro de diálogo cuando el usuario elige cambiar icono en el menú Editar o elige el botón Cambiar icono en los cuadros de diálogo Pegar especial o convertir. También se muestra cuando el usuario abre el cuadro de diálogo Insertar objeto y elige mostrar como icono. Use la clase [COleChangeIconDialog](../mfc/reference/colechangeicondialog-class.md) para mostrar este cuadro de diálogo.

*Verso*<br/>
Este cuadro de diálogo permite al usuario cambiar el tipo de un elemento incrustado o vinculado. Por ejemplo, si ha incrustado un metarchivo en un documento compuesto y posteriormente desea utilizar otra aplicación para modificar el metarchivo incrustado, puede utilizar el cuadro de diálogo convertir. Este cuadro de diálogo se muestra normalmente al hacer clic en objeto de *tipo de elemento* en el menú Editar y, a continuación, en el menú en cascada, haciendo clic en convertir. Use la clase [COleConvertDialog](../mfc/reference/coleconvertdialog-class.md) para mostrar este cuadro de diálogo. Para obtener un ejemplo, ejecute el ejemplo de OLE de MFC [OCLIENT](../overview/visual-cpp-samples.md).

*Editar vínculos o actualizar vínculos*<br/>
El cuadro de diálogo Editar vínculos permite al usuario cambiar la información sobre el origen de un objeto vinculado. En el cuadro de diálogo actualizar vínculos se comprueban los orígenes de todos los elementos vinculados en el cuadro de diálogo actual y se muestra el cuadro de diálogo Editar vínculos si es necesario. Muestra el cuadro de diálogo Editar vínculos cuando el usuario elige vínculos en el menú edición. Normalmente, el cuadro de diálogo actualizar vínculos se muestra cuando se abre por primera vez un documento compuesto. Use la clase [COleLinksDialog](../mfc/reference/colelinksdialog-class.md) o [COleUpdateDialog](../mfc/reference/coleupdatedialog-class.md) , en función del cuadro de diálogo que desee mostrar.

*Servidor ocupado o servidor no responde*<br/>
El cuadro de diálogo servidor ocupado se muestra cuando el usuario intenta activar un elemento y el servidor no puede controlar la solicitud, normalmente porque otro usuario o tarea está usando el servidor. Si el servidor no responde a la solicitud de activación, se muestra el cuadro de diálogo servidor que no responde. Estos cuadros de diálogo se muestran a través de `COleMessageFilter`, en función de una implementación de la interfaz OLE `IMessageFilter`, y el usuario puede decidir si desea volver a intentar la solicitud de activación. Use la clase [COleBusyDialog](../mfc/reference/colebusydialog-class.md) para mostrar este cuadro de diálogo.

## <a name="see-also"></a>Vea también

[Cuadros de diálogo](../mfc/dialog-boxes.md)<br/>
[Trabajar con cuadros de diálogo en MFC](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[OLE](../mfc/ole-in-mfc.md)
