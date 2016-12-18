---
title: "Agregar varias vistas a un solo documento | Microsoft Docs"
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
  - "documentos, varias vistas"
  - "varias vistas, SDI (aplicaciones)"
  - "interfaz de único documento (SDI), agregar vistas"
  - "vistas, SDI (aplicaciones)"
ms.assetid: 86d0c134-01d5-429c-b672-36cfb956dc01
caps.latest.revision: 13
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Agregar varias vistas a un solo documento
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En una aplicación creada de \(SDI\) de interfaz de un único documento con la biblioteca de \(MFC\) de la clase de la Microsoft foundation class, asociados a cada tipo de documento a un tipo de la vista única.  En algunos casos, es deseable tener la capacidad de cambiar la vista actual de un documento con una nueva vista.  
  
> [!TIP]
>  Para los procedimientos adicionales en implementar varias vistas para un único documento, vea [CDocument::AddView](../Topic/CDocument::AddView.md) y el ejemplo de [GET](../top/visual-cpp-samples.md) MFC.  
  
 Puede implementar esta funcionalidad agregar nuevo `CView`\- clase derivada y código adicional para intercambiar las vistas dinámicamente a una aplicación MFC existente.  
  
 Éstos son los pasos:  
  
-   [Modifique la clase de la aplicación existente](#vcconmodifyexistingapplicationa1)  
  
-   [Cree y Modifique la clase de la vista de Nuevo](#vcconnewviewclassa2)  
  
-   [Cree y asociar la vista New](#vcconattachnewviewa3)  
  
-   [Implemente la función de conmutación](#vcconswitchingfunctiona4)  
  
-   [Agregue compatibilidad para cambiar de vista](#vcconswitchingtheviewa5)  
  
 El resto de este tema se supone lo siguiente:  
  
-   El nombre de `CWinApp`\- el objeto derivado es `CMyWinApp`, y `CMyWinApp` se declara y se define en MYWINAPP.H y MYWINAPP.CPP.  
  
-   `CNewView` es el nombre de nuevo `CView`\- el objeto derivado, y `CNewView` se declara y se define en NEWVIEW.H y NEWVIEW.CPP.  
  
##  <a name="vcconmodifyexistingapplicationa1"></a> Modifique la clase de la aplicación existente  
 Para que la aplicación cambie entre las vistas, debe modificar la clase de aplicación agregando a variables miembro para almacenar las vistas y un método cambiar.  
  
 Agregue el código siguiente a la declaración de `CMyWinApp` en MYWINAPP.H:  
  
 [!code-cpp[NVC_MFCDocViewSDI#1](../mfc/codesnippet/CPP/adding-multiple-views-to-a-single-document_1.h)]  
  
 Nuevas variables miembros, `m_pOldView` y `m_pNewView`, elija la vista actual y el recién creado.  El nuevo método \(`SwitchView`\) cambia las vistas cuando es solicitado por el usuario.  El cuerpo del método se describe más adelante en este tema en [Implemente la función de conmutación](#vcconswitchingfunctiona4).  
  
 La modificación pasada a la clase de aplicación necesita con un nuevo archivo de encabezado que defina un mensaje de Windows \(**WM\_INITIALUPDATE**\) que se usa en la función de modificadores.  
  
 Inserte la línea siguiente en la sección de inclusión de MYWINAPP.CPP:  
  
 [!code-cpp[NVC_MFCDocViewSDI#2](../mfc/codesnippet/CPP/adding-multiple-views-to-a-single-document_2.cpp)]  
  
 Guarde los cambios y continúe con el paso siguiente.  
  
##  <a name="vcconnewviewclassa2"></a> Cree y Modifique la clase de la vista de Nuevo  
 Creando la nueva clase de vista se facilita utilizando el comando de **Nueva clase** disponibles en la vista de clases.  El único requisito para esta clase es que deriva de `CView`.  Agregue esta nueva clase a la aplicación.  Para obtener información concreta sobre cómo agregar una nueva clase al proyecto, vea [Agregar una clase](../ide/adding-a-class-visual-cpp.md).  
  
 Una vez que se ha agregado la clase al proyecto, debe cambiar la accesibilidad de algunos miembros de clase de vista.  
  
 Modifique NEWVIEW.H cambiando el especificador de acceso de `protected` a **público** para el constructor y el destructor.  Esto permite que destruyea la clase se crea y dinámicamente y modificar el aspecto de la vista antes de que esté visible.  
  
 Guarde los cambios y continúe con el paso siguiente.  
  
##  <a name="vcconattachnewviewa3"></a> Cree y asociar la vista New  
 Para crear y asociar la nueva vista, debe modificar la función de `InitInstance` de clase de aplicación.  La modificación agrega el nuevo código que crea un nuevo objeto de vista y se inicializa `m_pOldView` y `m_pNewView` con los dos objetos de vista existentes.  
  
 Dado que la nueva vista se crea dentro de la función de `InitInstance` , el nuevo y las vistas existentes conservan para la duración de la aplicación.  Sin embargo, la aplicación puede fácilmente crear la nueva vista dinámicamente.  
  
 Inserte este código después de la llamada a `ProcessShellCommand`:  
  
 [!code-cpp[NVC_MFCDocViewSDI#3](../mfc/codesnippet/CPP/adding-multiple-views-to-a-single-document_3.cpp)]  
  
 Guarde los cambios y continúe con el paso siguiente.  
  
##  <a name="vcconswitchingfunctiona4"></a> Implemente la función de conmutación  
 En el paso anterior, agrega el código que creó y inicializado un nuevo objeto de vista.  El fragmento principal pasado es implementar el método de conmutación, `SwitchView`.  
  
 Al final del archivo de implementación para la clase de aplicación \(MYWINAPP.CPP\), agregue la definición de método siguientes:  
  
 [!code-cpp[NVC_MFCDocViewSDI#4](../mfc/codesnippet/CPP/adding-multiple-views-to-a-single-document_4.cpp)]  
  
 Guarde los cambios y continúe con el paso siguiente.  
  
##  <a name="vcconswitchingtheviewa5"></a> Agregue compatibilidad para cambiar de vista  
 El paso final implica agregar el código que llama al método de `SwitchView` cuando la aplicación necesita cambiar entre las vistas.  Esto se puede hacer de varias maneras: agregar un nuevo elemento de menú para que el usuario elija o cambiando las vistas internamente cuando se cumplan ciertas condiciones.  
  
 Para obtener más información sobre cómo agregar nuevos elementos de menú y funciones de controlador de comandos, vea [Controladores para los comandos y notificaciones de Control](../mfc/handlers-for-commands-and-control-notifications.md).  
  
## Vea también  
 [Arquitectura documento\/vista](../mfc/document-view-architecture.md)