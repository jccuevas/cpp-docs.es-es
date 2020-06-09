---
title: Agregar varias vistas a un solo documento
ms.date: 11/04/2016
helpviewer_keywords:
- multiple views [MFC], SDI applications
- documents [MFC], multiple views
- single document interface (SDI), adding views
- views [MFC], SDI applications
ms.assetid: 86d0c134-01d5-429c-b672-36cfb956dc01
ms.openlocfilehash: 83bb7e54567319a7af4bd3d8a6bf02256fef68fb
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623356"
---
# <a name="adding-multiple-views-to-a-single-document"></a>Agregar varias vistas a un solo documento

En una aplicación de interfaz de un único documento (SDI) creada con la biblioteca MFC (Microsoft Foundation Class), cada tipo de documento está asociado a un tipo de vista único. En algunos casos, es deseable tener la posibilidad de cambiar la vista actual de un documento con una nueva vista.

> [!TIP]
> Para obtener más procedimientos sobre la implementación de varias vistas para un único documento, vea [CDocument:: AddView](reference/cdocument-class.md#addview) y el ejemplo [Collect](../overview/visual-cpp-samples.md) de MFC.

Puede implementar esta funcionalidad agregando una nueva `CView` clase derivada de y código adicional para cambiar las vistas dinámicamente a una aplicación MFC existente.

Los pasos son los siguientes:

- [Modificar la clase de aplicación existente](#vcconmodifyexistingapplicationa1)

- [Crear y modificar la nueva clase de vista](#vcconnewviewclassa2)

- [Crear y adjuntar la nueva vista](#vcconattachnewviewa3)

- [Implementar la función de cambio](#vcconswitchingfunctiona4)

- [Agregar compatibilidad para cambiar la vista](#vcconswitchingtheviewa5)

En el resto de este tema se da por supuesto lo siguiente:

- El nombre del `CWinApp` objeto derivado de es `CMyWinApp` , y `CMyWinApp` se declara y se define en *MYWINAPP. H* y *MYWINAPP. CPP*.

- `CNewView`es el nombre del nuevo `CView` objeto derivado de y `CNewView` se declara y se define en *NEWVIEW. H* y *NEWVIEW. CPP*.

## <a name="modify-the-existing-application-class"></a><a name="vcconmodifyexistingapplicationa1"></a>Modificar la clase de aplicación existente

Para que la aplicación cambie entre las vistas, debe modificar la clase de aplicación agregando variables de miembro para almacenar las vistas y un método para cambiarlas.

Agregue el código siguiente a la declaración de `CMyWinApp` en *MYWINAPP. H*:

[!code-cpp[NVC_MFCDocViewSDI#1](codesnippet/cpp/adding-multiple-views-to-a-single-document_1.h)]

Las nuevas variables de miembro, `m_pOldView` y `m_pNewView` , apuntan a la vista actual y a la recién creada. El nuevo método ( `SwitchView` ) cambia las vistas cuando lo solicita el usuario. El cuerpo del método se describe más adelante en este tema en [implementar la función de cambio](#vcconswitchingfunctiona4).

La última modificación de la clase de aplicación requiere incluir un nuevo archivo de encabezado que defina un mensaje de Windows (**WM_INITIALUPDATE**) que se usa en la función de cambio.

Inserte la siguiente línea en la sección include de *MYWINAPP. CPP*:

[!code-cpp[NVC_MFCDocViewSDI#2](codesnippet/cpp/adding-multiple-views-to-a-single-document_2.cpp)]

Guarde los cambios y continúe con el paso siguiente.

## <a name="create-and-modify-the-new-view-class"></a><a name="vcconnewviewclassa2"></a>Crear y modificar la nueva clase de vista

La creación de la nueva clase de vista se facilita mediante el comando **nueva clase** disponible en vista de clases. El único requisito de esta clase es que se deriva de `CView` . Agregue esta nueva clase a la aplicación. Para obtener información específica sobre cómo agregar una nueva clase al proyecto, vea [Agregar una clase](../ide/adding-a-class-visual-cpp.md).

Una vez que haya agregado la clase al proyecto, deberá cambiar la accesibilidad de algunos miembros de clase de vista.

Modifique *NEWVIEW. H* cambiando el especificador de acceso de **protegido** a **público** para el constructor y el destructor. Esto permite que la clase se cree y destruya dinámicamente y modifique la apariencia de la vista antes de que sea visible.

Guarde los cambios y continúe con el paso siguiente.

## <a name="create-and-attach-the-new-view"></a><a name="vcconattachnewviewa3"></a>Crear y adjuntar la nueva vista

Para crear y adjuntar la nueva vista, debe modificar la `InitInstance` función de la clase de la aplicación. La modificación agrega nuevo código que crea un nuevo objeto de vista y, a continuación, inicializa `m_pOldView` y `m_pNewView` con los dos objetos de vista existentes.

Dado que la nueva vista se crea dentro de la `InitInstance` función, las vistas nuevo y existente se conservan durante la vigencia de la aplicación. Sin embargo, la aplicación podría crear la nueva vista de forma sencilla y dinámica.

Inserte este código después de la llamada a `ProcessShellCommand` :

[!code-cpp[NVC_MFCDocViewSDI#3](codesnippet/cpp/adding-multiple-views-to-a-single-document_3.cpp)]

Guarde los cambios y continúe con el paso siguiente.

## <a name="implement-the-switching-function"></a><a name="vcconswitchingfunctiona4"></a>Implementar la función de cambio

En el paso anterior, agregó el código que creó e inicializó un nuevo objeto de vista. La última parte principal es implementar el método de cambio, `SwitchView` .

Al final del archivo de implementación de la clase de aplicación (*MYWINAPP. CPP*), agregue la siguiente definición de método:

[!code-cpp[NVC_MFCDocViewSDI#4](codesnippet/cpp/adding-multiple-views-to-a-single-document_4.cpp)]

Guarde los cambios y continúe con el paso siguiente.

## <a name="add-support-for-switching-the-view"></a><a name="vcconswitchingtheviewa5"></a>Agregar compatibilidad para cambiar la vista

El paso final implica agregar código que llama al `SwitchView` método cuando la aplicación necesita cambiar de una vista a otra. Esto se puede hacer de varias maneras: agregando un nuevo elemento de menú para que el usuario elija o cambie las vistas internamente cuando se cumplan determinadas condiciones.

Para obtener más información sobre cómo agregar nuevos elementos de menú y funciones de controlador de comandos, vea [Controladores para comandos y notificaciones de control](handlers-for-commands-and-control-notifications.md).

## <a name="see-also"></a>Consulte también

[Arquitectura documento/vista](document-view-architecture.md)
