---
title: Agregar varias vistas a un solo documento | Documentos de Microsoft
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
- multiple views [MFC], SDI applications
- documents [MFC], multiple views
- single document interface (SDI), adding views
- views [MFC], SDI applications
ms.assetid: 86d0c134-01d5-429c-b672-36cfb956dc01
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 865b30ac7b4c8910e92d14274f1224c25e7f74d8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="adding-multiple-views-to-a-single-document"></a>Agregar varias vistas a un solo documento
En una aplicación de interfaz de único documento (SDI) creada con la biblioteca (Microsoft Foundation Classes), cada tipo de documento está asociado con un tipo de vista única. En algunos casos, es conveniente tener la posibilidad de cambiar la vista actual de un documento con una nueva vista.  
  
> [!TIP]
>  Para obtener procedimientos adicionales sobre la implementación de varias vistas de un solo documento, vea [CDocument:: AddView](../mfc/reference/cdocument-class.md#addview) y [recopilar](../visual-cpp-samples.md) de MFC.  
  
 Puede implementar esta funcionalidad mediante la adición de un nuevo `CView`-derivados de clase y código adicional para cambiar las vistas dinámicamente a una aplicación MFC existente.  
  
 Los pasos son los siguientes:  
  
-   [Modifique la clase de aplicación existente](#vcconmodifyexistingapplicationa1)  
  
-   [Crear y modificar la nueva clase de vista](#vcconnewviewclassa2)  
  
-   [Crear y asociar la nueva vista](#vcconattachnewviewa3)  
  
-   [Implementar la función Switch](#vcconswitchingfunctiona4)  
  
-   [Agregar compatibilidad para cambiar la vista](#vcconswitchingtheviewa5)  
  
 El resto de este tema supone lo siguiente:  
  
-   El nombre de la `CWinApp`-objeto derivada es `CMyWinApp`, y `CMyWinApp` se declara y define en MYWINAPP. H y MYWINAPP. CPP.  
  
-   `CNewView`es el nombre del nuevo `CView`-objeto, derivado y `CNewView` se declara y define en NEWVIEW. H y NEWVIEW. CPP.  
  
##  <a name="vcconmodifyexistingapplicationa1"></a>Modifique la clase de aplicación existente  
 Para que cambiar entre las vistas de la aplicación, debe modificar la clase de aplicación agregando variables miembro para almacenar las vistas y un método para cambiarlas.  
  
 Agregue el código siguiente a la declaración de `CMyWinApp` en MYWINAPP. H:  
  
 [!code-cpp[NVC_MFCDocViewSDI#1](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_1.h)]  
  
 Las nuevas variables de miembro, `m_pOldView` y `m_pNewView`, seleccione la vista actual y el recién creado. El nuevo método (`SwitchView`) cambia las vistas cuando el usuario solicita. El cuerpo del método se explica más adelante en este tema en [implementar la función cambiar](#vcconswitchingfunctiona4).  
  
 La última modificación a la clase de aplicación requiere incluido un nuevo archivo de encabezado que define un mensaje de Windows (**WM_INITIALUPDATE**) que se utiliza en la función Switch.  
  
 Inserte la siguiente línea en la sección de inclusión de MYWINAPP. CPP:  
  
 [!code-cpp[NVC_MFCDocViewSDI#2](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_2.cpp)]  
  
 Guarde los cambios y continúe con el paso siguiente.  
  
##  <a name="vcconnewviewclassa2"></a>Crear y modificar la nueva clase de vista  
 Crear la nueva clase de vista se facilita mediante el uso de la **nueva clase** comandos disponibles en la vista de clases. El único requisito para esta clase es que se derive de `CView`. Agregar a esta nueva clase a la aplicación. Para obtener información específica acerca de cómo agregar una nueva clase al proyecto, vea [agregar una clase](../ide/adding-a-class-visual-cpp.md).  
  
 Cuando haya agregado la clase al proyecto, debe cambiar la accesibilidad de algunos miembros de clase de vista.  
  
 Modifique NEWVIEW. H cambiando el especificador de acceso de `protected` a **público** para el constructor y el destructor. Esto permite a la clase para crear y destruir de forma dinámica y modificar la apariencia de las vistas antes de que sea visible.  
  
 Guarde los cambios y continúe con el paso siguiente.  
  
##  <a name="vcconattachnewviewa3"></a>Crear y asociar la nueva vista  
 Para crear y asociar la nueva vista, debe modificar el `InitInstance` función de la clase de aplicación. La modificación agrega nuevo código que crea un nuevo objeto de vista y, a continuación, inicializa dos `m_pOldView` y `m_pNewView` con los dos objetos de vista existente.  
  
 Dado que la nueva vista se crea dentro de la `InitInstance` función, las vistas nuevas y existentes se conservan durante la vigencia de la aplicación. Sin embargo, la aplicación podría crear fácilmente la nueva vista dinámicamente.  
  
 Inserte este código después de llamar a `ProcessShellCommand`:  
  
 [!code-cpp[NVC_MFCDocViewSDI#3](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_3.cpp)]  
  
 Guarde los cambios y continúe con el paso siguiente.  
  
##  <a name="vcconswitchingfunctiona4"></a>Implementar la función Switch  
 En el paso anterior, agregó código que crea e inicializa un nuevo objeto de vista. La última parte importante consiste en implementar el método switch, `SwitchView`.  
  
 Al final del archivo de implementación para la clase de aplicación (MYWINAPP. (CPP), agregue la siguiente definición de método:  
  
 [!code-cpp[NVC_MFCDocViewSDI#4](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_4.cpp)]  
  
 Guarde los cambios y continúe con el paso siguiente.  
  
##  <a name="vcconswitchingtheviewa5"></a>Agregar compatibilidad para cambiar la vista  
 El último paso consiste en Agregar código que llama el `SwitchView` método cuando la aplicación debe pasar de una vista. Esto puede hacerse de varias maneras: agregando un nuevo elemento de menú para el usuario elija o cambiando las vistas internamente cuando se cumplen determinadas condiciones.  
  
 Para obtener más información sobre cómo agregar nuevos elementos de menú y las funciones de controlador de comandos, consulte [controladores de comandos y notificaciones del Control](../mfc/handlers-for-commands-and-control-notifications.md).  
  
## <a name="see-also"></a>Vea también  
 [Arquitectura documento/vista](../mfc/document-view-architecture.md)

