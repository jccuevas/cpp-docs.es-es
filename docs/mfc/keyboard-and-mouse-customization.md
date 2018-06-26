---
title: Personalización del teclado y mouse (ratón) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- customizations [MFC], keyboard and mouse (MFC Extensions)
- keyboard and mouse customizations (MFC Extensions)
ms.assetid: 1f789f1b-5f2e-4b11-b974-e3e2a2e49d82
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8fda670198dd9bd03a6d944ce4db70542926bf41
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36931585"
---
# <a name="keyboard-and-mouse-customization"></a>Personalización del teclado y del mouse
MFC permite al usuario de la aplicación para personalizar cómo controla el teclado y mouse de entrada. El usuario puede personalizar la entrada de teclado mediante la asignación de métodos abreviados de teclado para los comandos. El usuario también puede personalizar la entrada de mouse (ratón) seleccionando el comando que se debe ejecutar cuando el usuario hace doble clic dentro de windows específicos de la aplicación. En este tema se explica cómo personalizar la entrada de la aplicación.  
  
 En el **personalización** cuadro de diálogo, el usuario puede cambiar los controles personalizados para el mouse y el teclado. Para mostrar este cuadro de diálogo, el usuario apunta a **personalizar** en el **vista** menú y, a continuación, hace clic en **acoplamiento y barras de herramientas**. En el cuadro de diálogo, el usuario hace clic en el **teclado** ficha o el **Mouse** ficha.  
  
## <a name="keyboard-customization"></a>Personalización del teclado  
 La siguiente ilustración muestra la **teclado** pestaña de la **personalización** cuadro de diálogo.  
  
 ![Pestaña teclado en el cuadro de diálogo Personalizar](../mfc/media/mfcnextkeyboardtab.png "mfcnextkeyboardtab")  
Ficha de personalización del teclado  
  
 El usuario interactúa con la tabulación de teclado para asignar uno o más métodos abreviados de teclado a un comando. Los comandos disponibles se muestran en el lado izquierdo de la pestaña. El usuario puede seleccionar cualquier comando disponible en el menú. Comandos de menú sólo pueden asociarse con un método abreviado de teclado. Cuando el usuario introduce un nuevo acceso directo, el **asignar** botón se habilita. Cuando el usuario hace clic en este botón, la aplicación asocia el comando seleccionado a ese método abreviado.  
  
 Todos los métodos abreviados de teclado actualmente asignados se muestran en el cuadro de lista en la columna derecha. El usuario también puede seleccionar accesos directos individuales y quitarlos o restablecer todas las asignaciones para la aplicación.  
  
 Si desea admitir esta personalización en la aplicación, debe crear un [CKeyboardManager](../mfc/reference/ckeyboardmanager-class.md) objeto. Para crear un `CKeyboardManager` de objeto, llame a la función [CWinAppEx::InitKeyboardManager](../mfc/reference/cwinappex-class.md#initkeyboardmanager). Este método crea e inicializa el Administrador de un teclado. Si creas un teclado manager manualmente, todavía debe llamar a `CWinAppEx::InitKeyboardManager` para inicializarlo.  
  
 Si utiliza al Asistente para crear la aplicación, el Asistente inicializará el Administrador de teclado. Después de que la aplicación inicializa el Administrador de teclado, el marco de trabajo agrega un **teclado** tabulador para ir a la **personalización** cuadro de diálogo.  
  
## <a name="mouse-customization"></a>Personalización del mouse  
 La siguiente ilustración muestra la **Mouse** pestaña de la **personalización** cuadro de diálogo.  
  
 ![Pestaña mouse (ratón) en el cuadro de diálogo Personalizar](../mfc/media/mfcnextmousetab.png "mfcnextmousetab")  
En la ficha personalización del mouse  
  
 El usuario interactúa con esta ficha para asignar un menú de comandos para el mouse, haga doble clic en acción. El usuario selecciona una vista del lado izquierdo de la ventana y, a continuación, utiliza los controles en el lado derecho para asociar un comando con la acción de doble clic. Después de que el usuario hace clic en **cerrar**, la aplicación ejecuta el comando asociado cada vez que el usuario hace doble clic en cualquier lugar en la vista.  
  
 De forma predeterminada, personalización del mouse (ratón) no está habilitado cuando se crea una aplicación mediante el asistente.  
  
#### <a name="to-enable-mouse-customization"></a>Para habilitar la personalización del mouse  
  
1.  Inicializar un [CMouseManager](../mfc/reference/cmousemanager-class.md) objeto mediante una llamada a [CWinAppEx::InitMouseManager](../mfc/reference/cwinappex-class.md#initmousemanager).  
  
2.  Obtener un puntero al administrador del mouse mediante [CWinAppEx::GetMouseManager](../mfc/reference/cwinappex-class.md#getmousemanager).  
  
3.  Agregar vistas al administrador del mouse mediante el [CMouseManager::AddView](../mfc/reference/cmousemanager-class.md#addview) método. Hágalo para todas las vistas que desea agregar al administrador de mouse (ratón).  
  
 Después de que la aplicación inicializa el Administrador de mouse (ratón), el marco de trabajo agrega la **Mouse** tabulador para ir a la **personalizar** cuadro de diálogo. Si no agrega todas las vistas, obtener acceso a la ficha provocará una excepción no controlada. Después de haber creado una lista de vistas, el **Mouse** pestaña está disponible para el usuario.  
  
 Cuando se agrega una nueva vista en el administrador del mouse, se proporciona un identificador único. Si desea que admite la personalización de mouse (ratón) de una ventana, debe procesar el mensaje WM_LBUTTONDBLCLICK y llame a la [CWinAppEx::OnViewDoubleClick](../mfc/reference/cwinappex-class.md#onviewdoubleclick) (función). Cuando se llama a esta función, uno de los parámetros es el identificador de esa ventana. Es responsabilidad del programador para realizar un seguimiento de los números de identificador y los objetos asociados con ellos.  
  
## <a name="security-concerns"></a>Cuestiones de seguridad  
 Como se describe en [herramientas definidas por el usuario](../mfc/user-defined-tools.md), el usuario puede asociar un identificador de herramienta definido por el usuario con el evento de doble clic. Cuando el usuario hace doble clic en una vista, la aplicación busca una herramienta de usuario que coincida con el identificador asociado. Si la aplicación encuentra una herramienta de búsqueda de coincidencias, ejecuta la herramienta. Si la aplicación no puede encontrar una herramienta de búsqueda de coincidencias, envía un mensaje WM_COMMAND con el identificador a la vista que se hizo doble clic.  
  
 La configuración personalizada se almacena en el registro. Si modifica el registro, un atacante puede reemplazar un identificador de la herramienta de usuario válido con un comando arbitrario. Cuando el usuario hace doble clic en una vista, la vista procesa el comando que el atacante ocupado. Esto podría provocar un comportamiento inesperado y potencialmente peligroso.  
  
 Además, este tipo de ataque puede omitir las medidas de seguridad de interfaz de usuario. Por ejemplo, suponga que una aplicación tiene deshabilitada la impresión. Es decir, en la interfaz de usuario, el **impresión** menú y botón no están disponibles. Normalmente esto impide que la aplicación de impresión. Pero si un atacante había editado el registro, un usuario podría ahora puede enviar el comando de impresión directamente haciendo doble clic en la vista, omitiendo los elementos de la interfaz de usuario que no están disponibles.  
  
 Para protegerse de este tipo de ataque, agregue código a su controlador de comandos de la aplicación para comprobar que un comando es válido antes de que se ejecute. No dependen de la interfaz de usuario para impedir que un comando que se envía a la aplicación.  
  
## <a name="see-also"></a>Vea también  
 [Personalización de MFC](../mfc/customization-for-mfc.md)   
 [Clase CKeyboardManager](../mfc/reference/ckeyboardmanager-class.md)   
 [Clase CMouseManager](../mfc/reference/cmousemanager-class.md)   
 [Implicaciones de seguridad de la personalización](../mfc/security-implications-of-customization.md)

