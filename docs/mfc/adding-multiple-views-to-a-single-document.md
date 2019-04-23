---
title: Agregar varias vistas a un solo documento
ms.date: 11/04/2016
helpviewer_keywords:
- multiple views [MFC], SDI applications
- documents [MFC], multiple views
- single document interface (SDI), adding views
- views [MFC], SDI applications
ms.assetid: 86d0c134-01d5-429c-b672-36cfb956dc01
ms.openlocfilehash: 593c59c73b58b4364c9d652ce8eb415c17af496c
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "58767592"
---
# <a name="adding-multiple-views-to-a-single-document"></a>Agregar varias vistas a un solo documento

En una aplicación de interfaz de único documento (SDI) creada con la biblioteca Microsoft Foundation Class (MFC), cada tipo de documento está asociado con un tipo de vista única. En algunos casos, es recomendable tener la posibilidad de cambiar la vista actual de un documento con una nueva vista.

> [!TIP]
>  Para obtener procedimientos adicionales sobre la implementación de varias vistas para un único documento, vea [CDocument:: AddView](../mfc/reference/cdocument-class.md#addview) y [recopilar](../overview/visual-cpp-samples.md) ejemplo de MFC.

Puede implementar esta funcionalidad mediante la adición de un nuevo `CView`-derivados de clase y código adicional para cambiar las vistas de forma dinámica a una aplicación MFC existente.

Los pasos son los siguientes:

- [Modifique la clase de aplicación existente](#vcconmodifyexistingapplicationa1)

- [Crear y modificar la nueva clase de vista](#vcconnewviewclassa2)

- [Crear y asociar la nueva vista](#vcconattachnewviewa3)

- [Implementar la función Switch](#vcconswitchingfunctiona4)

- [Agregar compatibilidad para cambiar la vista](#vcconswitchingtheviewa5)

El resto de este tema se da por supuesto lo siguiente:

- El nombre de la `CWinApp`-objeto derivado es `CMyWinApp`, y `CMyWinApp` se declaran y definen en *MYWINAPP. H* y *MYWINAPP. CPP*.

- `CNewView` es el nombre del nuevo `CView`-objeto, derivado y `CNewView` se declaran y definen en *NEWVIEW. H* y *NEWVIEW. CPP*.

##  <a name="vcconmodifyexistingapplicationa1"></a> Modifique la clase de aplicación existente

Para que cambiar entre las vistas de la aplicación, deberá modificar la clase de aplicación mediante la adición de variables de miembro para almacenar las vistas y un método para cambiarlas.

Agregue el código siguiente a la declaración de `CMyWinApp` en *MYWINAPP. H*:

[!code-cpp[NVC_MFCDocViewSDI#1](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_1.h)]

Las nuevas variables de miembro, `m_pOldView` y `m_pNewView`, apunte a la vista actual y uno recién creado. El nuevo método (`SwitchView`) cambia las vistas cuando se ha solicitado el usuario. El cuerpo del método se explica más adelante en este tema en [implementar la función conmutación](#vcconswitchingfunctiona4).

La última modificación a la clase de aplicación requiere incluyendo un nuevo archivo de encabezado que define un mensaje de Windows (**WM_INITIALUPDATE**) que se utiliza en la función Switch.

Inserte la siguiente línea en la sección include de *MYWINAPP. CPP*:

[!code-cpp[NVC_MFCDocViewSDI#2](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_2.cpp)]

Guarde los cambios y continúe con el paso siguiente.

##  <a name="vcconnewviewclassa2"></a> Crear y modificar la nueva clase de vista

Creación de la nueva clase de vista es fácil mediante el uso de la **nueva clase** comando disponible en vista de clases. El único requisito para esta clase es que se deriva de `CView`. Agregue esta nueva clase a la aplicación. Para obtener información específica acerca de cómo agregar una nueva clase al proyecto, vea [agregar una clase](../ide/adding-a-class-visual-cpp.md).

Una vez haya agregado la clase al proyecto, deberá cambiar la accesibilidad de algunos miembros de clase de vista.

Modificar *NEWVIEW. H* cambiando el especificador de acceso de **protegido** a **pública** para el constructor y destructor. Esto permite a la clase para crear y destruir de forma dinámica y modificar la apariencia de la vista antes de que sea visible.

Guarde los cambios y continúe con el paso siguiente.

##  <a name="vcconattachnewviewa3"></a> Crear y asociar la nueva vista

Para crear y asociar la nueva vista, deberá modificar el `InitInstance` función de la clase de aplicación. La modificación agrega nuevo código que crea un nuevo objeto de vista y, a continuación, inicializa ambas `m_pOldView` y `m_pNewView` con los dos objetos de vista existentes.

Dado que la nueva vista se crea dentro de la `InitInstance` función, las vistas nuevas y existentes se conservan durante la vigencia de la aplicación. Sin embargo, la aplicación podría crear fácilmente la nueva vista de forma dinámica.

Inserte este código después de llamar a `ProcessShellCommand`:

[!code-cpp[NVC_MFCDocViewSDI#3](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_3.cpp)]

Guarde los cambios y continúe con el paso siguiente.

##  <a name="vcconswitchingfunctiona4"></a> Implementar la función Switch

En el paso anterior, agregó un código que crea e inicializa un nuevo objeto de vista. La última parte importante consiste en implementar el método switch, `SwitchView`.

Al final del archivo de implementación para la clase de aplicación (*MYWINAPP. CPP*), agregue la siguiente definición de método:

[!code-cpp[NVC_MFCDocViewSDI#4](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_4.cpp)]

Guarde los cambios y continúe con el paso siguiente.

##  <a name="vcconswitchingtheviewa5"></a> Agregar compatibilidad para cambiar la vista

El último paso consiste en Agregar código que llama a la `SwitchView` método cuando la aplicación necesita para cambiar entre vistas. Esto puede realizarse de varias maneras: agregando un nuevo elemento de menú para el usuario pueda elegir o cambiar las vistas internamente cuando se cumplen ciertas condiciones.

Para obtener más información sobre cómo agregar nuevos elementos de menú y las funciones de controlador de comandos, consulte [controladores de comandos y notificaciones del Control](../mfc/handlers-for-commands-and-control-notifications.md).

## <a name="see-also"></a>Vea también

[Arquitectura documento/vista](../mfc/document-view-architecture.md)
