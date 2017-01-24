---
title: "Personalizaci&#243;n del teclado y del mouse | Microsoft Docs"
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
  - "personalizaciones, teclado y mouse (extensiones MFC)"
  - "personalizaciones del teclado y del mouse (extensiones MFC)"
ms.assetid: 1f789f1b-5f2e-4b11-b974-e3e2a2e49d82
caps.latest.revision: 23
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Personalizaci&#243;n del teclado y del mouse
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC permite al usuario de la aplicación para personalizar cómo controla la entrada de teclado y mouse.  El usuario puede personalizar entrada de teclado asignando los métodos abreviados de teclado para los comandos.  El usuario también puede personalizar el mouse escrito seleccionando el comando que debe ejecutarse cuando el usuario hace doble clic dentro de las ventanas específicas de la aplicación.  Este tema explica cómo personalizar la entrada de la aplicación.  
  
 En el cuadro de diálogo de **Personalización** , el usuario puede cambiar los controles personalizados del mouse y el teclado.  Para mostrar este cuadro de diálogo, los puntos del usuario a **Personaliz** en el menú de **Visualización** y haga clic en **Barras de herramientas y acoplamiento**.  En el cuadro de diálogo, el usuario hace clic en la ficha de **Teclado** o la ficha de **Mouse** .  
  
## Personalización de teclado  
 La siguiente ilustración muestra la pestaña de **Teclado** del cuadro de diálogo de **Personalización** .  
  
 ![Pestaña Teclado del cuadro de diálogo Personalizar](../mfc/media/mfcnextkeyboardtab.png "MFCNextKeyboardTab")  
Pestaña de personalización de teclado  
  
 El usuario interactúa con la pestaña teclado para asignar uno o más métodos abreviados de teclado a un comando.  Se enumeran los comandos disponibles en el lado izquierdo de la ficha.  El usuario puede seleccionar cualquier comando disponible en el menú.  Únicamente los comandos de menú pueden estar asociados a un método abreviado de teclado.  Después de que el usuario especifique un nuevo acceso directo, el botón de **Asignar** aparece deshabilitado.  Cuando el usuario hace clic en este botón, la aplicación asocia el comando seleccionado a dicho acceso directo.  
  
 Todos los métodos abreviados de teclado actualmente asignados aparecen en el cuadro de lista de la columna derecha.  El usuario puede seleccionar también accesos directos individuales y quitarlos, o restaurar todas las asignaciones para la aplicación.  
  
 Si desea admitir esta personalización en la aplicación, debe crear un objeto de [CKeyboardManager](../mfc/reference/ckeyboardmanager-class.md) .  Para crear un objeto de `CKeyboardManager` , llame a la función [CWinAppEx::InitKeyboardManager](../Topic/CWinAppEx::InitKeyboardManager.md).  Este método crea e inicializa un administrador de teclado.  Si crea un administrador de teclado manualmente, todavía debe llamar a `CWinAppEx::InitKeyboardManager` para inicializarla.  
  
 Si utiliza el asistente para crear la aplicación, el asistente se inicializará el administrador de teclado.  Después de que se inicialice la aplicación el administrador del teclado, el marco agrega una pestaña de **Teclado** al cuadro de diálogo de **Personalización** .  
  
## Personalización del mouse  
 La siguiente ilustración muestra la pestaña de **Mouse** del cuadro de diálogo de **Personalización** .  
  
 ![Pestaña Mouse del cuadro de diálogo Personalizar](../mfc/media/mfcnextmousetab.png "MFCNextMouseTab")  
Pestaña de personalización del mouse  
  
 El usuario interactúa con esta pestaña para asignar un comando de menú a la acción de doble clic del mouse.  El usuario selecciona una vista del lado izquierdo de la ventana y después utilizar los controles en el lado derecho para asociar un comando con la acción de doble clic.  Después de que el usuario haga clic en **cerrar**, la aplicación ejecuta el comando asociado cada vez que el usuario haga doble clic en cualquier parte de la vista.  
  
 De forma predeterminada, la personalización del mouse no se habilita cuando se crea una aplicación mediante el asistente.  
  
#### Para habilitar la personalización del mouse  
  
1.  Inicializa un objeto de [CMouseManager](../mfc/reference/cmousemanager-class.md) llamando a [CWinAppEx::InitMouseManager](../Topic/CWinAppEx::InitMouseManager.md).  
  
2.  Obtenga un puntero al administrador del mouse utilizando [CWinAppEx::GetMouseManager](../Topic/CWinAppEx::GetMouseManager.md).  
  
3.  Agregue las vistas al administrador del mouse utilizando el método de [CMouseManager::AddView](../Topic/CMouseManager::AddView.md) .  Haga esto para cada vista que desea agregar al administrador del mouse.  
  
 Después de que se inicialice la aplicación el administrador del mouse, el marco agrega la pestaña de **Mouse** al cuadro de diálogo de **Personaliz** .  Si no agrega ninguna vistas, el acceso de la pestaña producirá una excepción no controlada.  Después de crear una lista de vistas, la ficha de **Mouse** está disponible al usuario.  
  
 Cuando se agrega una nueva vista el administrador del mouse, se le asigna un identificador único  Si desea admitir la personalización de mouse para una ventana, debe procesar el mensaje de `WM_LBUTTONDBLCLICK` y llamar a la función de [CWinAppEx::OnViewDoubleClick](../Topic/CWinAppEx::OnViewDoubleClick.md) .  Cuando se llama a esta función, uno de los parámetros es el identificador de esa ventana.  Es responsabilidad del programador hacer un seguimiento de los números de identificación y los objetos asociados a ellos.  
  
## Cuestiones de seguridad  
 Como se describe en [Herramientas definidas por el usuario](../mfc/user-defined-tools.md), puede asociar un identificador de herramienta definido por el usuario con el evento de doble clic.  Cuando el usuario hace doble clic en una vista, la aplicación busca una herramienta de usuario que coincida con la identificación asociada  Si la aplicación encuentra una herramienta coincidente, se ejecuta la herramienta.  Si la aplicación no puede encontrar una herramienta coincidente, envía un mensaje WM\_COMMAND con el identificador de la vista que doble\- hizo clic.  
  
 Los valores personalizados se almacena en el registro.  Editar el registro, un atacante puede reemplazar un identificador del usuario válido con un comando arbitrario.  Cuando el usuario hace doble clic en una vista, la vista procesa el comando que el atacante plantó.  Esto puede producir un comportamiento inesperado y potencialmente peligroso.  
  
 Además, este tipo de ataque puede omitir las medidas de seguridad de la interfaz de usuario.  Por ejemplo, supongamos que una aplicación tiene impresión deshabilitada.  Es decir, en la interfaz de usuario, el menú de **Impresión** y el botón no están disponibles.  Esto evita normalmente la aplicación de impresión.  Pero si un atacante editó el registro, un usuario podría ahora puede enviar el comando de impresión directamente haciendo doble clic en la vista, omitiendo los elementos de la interfaz de usuario que no están disponibles.  
  
 Para protegerse de este tipo de ataque, agregue código al controlador de comandos de la aplicación para comprobar que un comando es válido antes de ejecutarse.  No dependa de la interfaz de usuario para evitar enviar un comando a la aplicación.  
  
## Vea también  
 [Personalización de MFC](../mfc/customization-for-mfc.md)   
 [CKeyboardManager Class](../mfc/reference/ckeyboardmanager-class.md)   
 [CMouseManager Class](../mfc/reference/cmousemanager-class.md)   
 [Implicaciones de seguridad de la personalización](../mfc/security-implications-of-customization.md)