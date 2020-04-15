---
title: Agregar varias vistas a un solo documento
ms.date: 11/04/2016
helpviewer_keywords:
- multiple views [MFC], SDI applications
- documents [MFC], multiple views
- single document interface (SDI), adding views
- views [MFC], SDI applications
ms.assetid: 86d0c134-01d5-429c-b672-36cfb956dc01
ms.openlocfilehash: 4fa39a4d9369c84d2cffdaeff28dc9cb2f966b31
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370866"
---
# <a name="adding-multiple-views-to-a-single-document"></a>Agregar varias vistas a un solo documento

En una aplicación de interfaz de documento único (SDI) creada con la biblioteca de Microsoft Foundation Class (MFC), cada tipo de documento está asociado a un único tipo de vista. En algunos casos, es deseable tener la capacidad de cambiar la vista actual de un documento con una nueva vista.

> [!TIP]
> Para obtener procedimientos adicionales sobre la implementación de varias vistas para un único documento, vea [CDocument::AddView](../mfc/reference/cdocument-class.md#addview) y el [ejemplo de MFC COLLECT.](../overview/visual-cpp-samples.md)

Puede implementar esta funcionalidad agregando `CView`una nueva clase derivada y código adicional para cambiar las vistas dinámicamente a una aplicación MFC existente.

Los pasos son los siguientes:

- [Modificar la clase de aplicación existente](#vcconmodifyexistingapplicationa1)

- [Crear y modificar la nueva clase de vista](#vcconnewviewclassa2)

- [Crear y adjuntar la nueva vista](#vcconattachnewviewa3)

- [Implementar la función de conmutación](#vcconswitchingfunctiona4)

- [Agregar soporte para cambiar la vista](#vcconswitchingtheviewa5)

El resto de este tema supone lo siguiente:

- El nombre `CWinApp`del objeto -derived es `CMyWinApp`, y `CMyWinApp` se declara y define en *MYWINAPP. H* y *MYWINAPP. CPP*.

- `CNewView`es el nombre `CView`del nuevo objeto `CNewView` derivado y se declara y define en *NEWVIEW. H* y *NEWVIEW. CPP*.

## <a name="modify-the-existing-application-class"></a><a name="vcconmodifyexistingapplicationa1"></a>Modificar la clase de aplicación existente

Para que la aplicación cambie entre vistas, debe modificar la clase de aplicación agregando variables miembro para almacenar las vistas y un método para cambiarlas.

Agregue el código siguiente `CMyWinApp` a la declaración de *myWINAPP. H*:

[!code-cpp[NVC_MFCDocViewSDI#1](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_1.h)]

Las nuevas variables miembro `m_pOldView` y `m_pNewView`, apuntan a la vista actual y a la recién creada. El nuevo`SwitchView`método ( ) cambia las vistas cuando lo solicita el usuario. El cuerpo del método se describe más adelante en este tema en [Implementar la función de conmutación](#vcconswitchingfunctiona4).

La última modificación de la clase de aplicación requiere incluir un nuevo archivo de encabezado que define un mensaje de Windows (**WM_INITIALUPDATE**) que se utiliza en la función de conmutación.

Inserte la siguiente línea en la sección include de *MYWINAPP. CPP*:

[!code-cpp[NVC_MFCDocViewSDI#2](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_2.cpp)]

Guarde los cambios y continúe con el paso siguiente.

## <a name="create-and-modify-the-new-view-class"></a><a name="vcconnewviewclassa2"></a>Crear y modificar la nueva clase de vista

La creación de la nueva clase de vista se facilita mediante el comando **Nueva clase** disponible en la vista de clases. El único requisito para esta clase `CView`es que deriva de . Agregue esta nueva clase a la aplicación. Para obtener información específica sobre cómo agregar una nueva clase al proyecto, vea [Agregar una clase](../ide/adding-a-class-visual-cpp.md).

Una vez que haya agregado la clase al proyecto, debe cambiar la accesibilidad de algunos miembros de la clase de vista.

Modificar *NEWVIEW. H* cambiando el especificador de acceso de **protegido** a **público** para el constructor y el destructor. Esto permite que la clase se cree y destruya dinámicamente y modifique el aspecto de la vista antes de que sea visible.

Guarde los cambios y continúe con el paso siguiente.

## <a name="create-and-attach-the-new-view"></a><a name="vcconattachnewviewa3"></a>Crear y adjuntar la nueva vista

Para crear y adjuntar la nueva vista, debe modificar la función de la `InitInstance` clase de aplicación. La modificación agrega código nuevo que crea un `m_pOldView` nuevo `m_pNewView` objeto de vista y, a continuación, inicializa ambos y con los dos objetos de vista existentes.

Dado que la nueva `InitInstance` vista se crea dentro de la función, las vistas nuevas y existentes persisten durante la duración de la aplicación. Sin embargo, la aplicación podría crear la nueva vista con la misma facilidad dinámicamente.

Inserte este código después de la llamada a: `ProcessShellCommand`

[!code-cpp[NVC_MFCDocViewSDI#3](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_3.cpp)]

Guarde los cambios y continúe con el paso siguiente.

## <a name="implement-the-switching-function"></a><a name="vcconswitchingfunctiona4"></a>Implementar la función de conmutación

En el paso anterior, agregó código que creó e inicializó un nuevo objeto de vista. La última pieza importante es implementar `SwitchView`el método de conmutación, .

Al final del archivo de implementación para la clase de aplicación (*MYWINAPP. CPP*), añada la siguiente definición de método:

[!code-cpp[NVC_MFCDocViewSDI#4](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_4.cpp)]

Guarde los cambios y continúe con el paso siguiente.

## <a name="add-support-for-switching-the-view"></a><a name="vcconswitchingtheviewa5"></a>Agregar soporte para cambiar la vista

El paso final implica agregar `SwitchView` código que llama al método cuando la aplicación necesita cambiar entre vistas. Esto se puede hacer de varias maneras: agregando un nuevo elemento de menú para que el usuario elija o cambiando las vistas internamente cuando se cumplen ciertas condiciones.

Para obtener más información sobre cómo agregar nuevos elementos de menú y funciones de controlador de comandos, vea [Controladores de comandos y notificaciones](../mfc/handlers-for-commands-and-control-notifications.md)de control .

## <a name="see-also"></a>Consulte también

[Arquitectura de documento/vista](../mfc/document-view-architecture.md)
