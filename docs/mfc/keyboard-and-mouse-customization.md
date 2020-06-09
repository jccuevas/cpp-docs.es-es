---
title: Personalización del teclado y del mouse
ms.date: 11/19/2018
helpviewer_keywords:
- customizations [MFC], keyboard and mouse (MFC Extensions)
- keyboard and mouse customizations (MFC Extensions)
ms.assetid: 1f789f1b-5f2e-4b11-b974-e3e2a2e49d82
ms.openlocfilehash: 262555b060f226a86438a2189eda44d83c55d5a2
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621503"
---
# <a name="keyboard-and-mouse-customization"></a>Personalización del teclado y del mouse

MFC permite al usuario de la aplicación personalizar Cómo controla la entrada del teclado y del mouse. El usuario puede personalizar la entrada del teclado mediante la asignación de métodos abreviados de teclado a comandos. El usuario también puede personalizar la entrada del mouse seleccionando el comando que debe ejecutarse cuando el usuario hace doble clic en las ventanas específicas de la aplicación. En este tema se explica cómo personalizar la entrada para la aplicación.

En el cuadro de diálogo **Personalización** , el usuario puede cambiar los controles personalizados para el mouse y el teclado. Para mostrar este cuadro de diálogo, el usuario apunta a **personalizar** en el menú **Ver** y, a continuación, hace clic en **barras de herramientas y acoplamiento**. En el cuadro de diálogo, el usuario hace clic en la pestaña **teclado** o en la pestaña **mouse** .

## <a name="keyboard-customization"></a>Personalización del teclado

En la ilustración siguiente se muestra la pestaña **teclado** del cuadro de diálogo de **Personalización** .

![Pestaña Teclado del cuadro de diálogo Personalizar](../mfc/media/mfcnextkeyboardtab.png "Pestaña Teclado del cuadro de diálogo Personalizar") <br/>
Pestaña personalización del teclado

El usuario interactúa con la pestaña teclado para asignar uno o varios métodos abreviados de teclado a un comando. Los comandos disponibles se enumeran en el lado izquierdo de la pestaña. El usuario puede seleccionar cualquier comando disponible en el menú. Solo se pueden asociar comandos de menú a un método abreviado de teclado. Una vez que el usuario escribe un nuevo acceso directo, se habilita el botón **asignar** . Cuando el usuario hace clic en este botón, la aplicación asocia el comando seleccionado con ese acceso directo.

Todos los métodos abreviados de teclado asignados actualmente se muestran en el cuadro de lista de la columna derecha. El usuario también puede seleccionar accesos directos individuales y quitarlos, o restablecer todas las asignaciones de la aplicación.

Si desea admitir esta personalización en la aplicación, debe crear un objeto [CKeyboardManager](reference/ckeyboardmanager-class.md) . Para crear un `CKeyboardManager` objeto, llame a la función [CWinAppEx:: InitKeyboardManager](reference/cwinappex-class.md#initkeyboardmanager). Este método crea e inicializa un administrador de teclado. Si crea un administrador de teclado manualmente, debe llamar `CWinAppEx::InitKeyboardManager` a para inicializarlo.

Si usa el Asistente para crear la aplicación, el asistente inicializará el administrador de teclado. Una vez que la aplicación inicializa el administrador de teclado, el marco de trabajo agrega una ficha de **teclado** al cuadro de diálogo de **Personalización** .

## <a name="mouse-customization"></a>Personalización del mouse

En la ilustración siguiente se muestra la pestaña **mouse** del cuadro de diálogo de **Personalización** .

![Pestaña Mouse del cuadro de diálogo Personalizar](../mfc/media/mfcnextmousetab.png "Pestaña Mouse del cuadro de diálogo Personalizar") <br/>
Pestaña personalización del mouse

El usuario interactúa con esta pestaña para asignar un comando de menú a la acción de doble clic del mouse. El usuario selecciona una vista en el lado izquierdo de la ventana y, a continuación, usa los controles del lado derecho para asociar un comando con la acción de doble clic. Una vez que el usuario hace clic en **cerrar**, la aplicación ejecuta el comando asociado cada vez que el usuario hace doble clic en cualquier parte de la vista.

De forma predeterminada, la personalización del mouse no está habilitada cuando se crea una aplicación mediante el asistente.

#### <a name="to-enable-mouse-customization"></a>Para habilitar la personalización del mouse

1. Inicialice un objeto [CMouseManager](reference/cmousemanager-class.md) llamando a [CWinAppEx:: InitMouseManager](reference/cwinappex-class.md#initmousemanager).

1. Obtenga un puntero al administrador del mouse mediante [CWinAppEx:: GetMouseManager](reference/cwinappex-class.md#getmousemanager).

1. Agregue vistas al administrador del mouse mediante el método [CMouseManager:: AddView](reference/cmousemanager-class.md#addview) . Haga esto por cada vista que desee agregar al administrador del mouse.

Una vez que la aplicación haya inicializado el administrador del mouse, el marco de trabajo agrega la pestaña **mouse** al cuadro de diálogo **personalizar** . Si no agrega ninguna vista, el acceso a la pestaña producirá una excepción no controlada. Después de crear una lista de vistas, la pestaña **mouse** está disponible para el usuario.

Cuando se agrega una nueva vista al administrador del mouse, se le asigna un identificador único. Si desea admitir la personalización del mouse para una ventana, debe procesar el mensaje de WM_LBUTTONDBLCLICK y llamar a la función [CWinAppEx:: OnViewDoubleClick](reference/cwinappex-class.md#onviewdoubleclick) . Cuando se llama a esta función, uno de los parámetros es el identificador de la ventana. Es responsabilidad del programador realizar un seguimiento de los números de identificador y de los objetos asociados a ellos.

## <a name="security-concerns"></a>Cuestiones de seguridad

Como se describe en [herramientas definidas por el usuario](user-defined-tools.md), el usuario puede asociar un identificador de herramienta definido por el usuario con el evento de doble clic. Cuando el usuario hace doble clic en una vista, la aplicación busca una herramienta de usuario que coincida con el identificador asociado. Si la aplicación encuentra una herramienta coincidente, ejecuta la herramienta. Si la aplicación no encuentra una herramienta coincidente, envía un mensaje de WM_COMMAND con el identificador a la vista en la que se hizo doble clic.

La configuración personalizada se almacena en el registro. Al editar el registro, un atacante puede reemplazar un identificador de herramienta de usuario válido por un comando arbitrario. Cuando el usuario hace doble clic en una vista, la vista procesa el comando que el atacante ha plantado. Esto podría provocar un comportamiento inesperado y potencialmente peligroso.

Además, este tipo de ataque puede omitir las medidas de seguridad de la interfaz de usuario. Por ejemplo, supongamos que una aplicación tiene deshabilitada la impresión. Es decir, en su interfaz de usuario, el menú de **impresión** y el botón no están disponibles. Normalmente esto evita que la aplicación se imprima. Pero si un atacante ha editado el registro, el usuario podría enviar el comando de impresión directamente haciendo doble clic en la vista, omitiendo los elementos de la interfaz de usuario que no están disponibles.

Para protegerse contra este tipo de ataque, agregue código al controlador de comandos de la aplicación para comprobar que un comando es válido antes de que se ejecute. No dependa de la interfaz de usuario para evitar que se envíe un comando a la aplicación.

## <a name="see-also"></a>Consulte también

[Personalización de MFC](customization-for-mfc.md)<br/>
[Clase CKeyboardManager](reference/ckeyboardmanager-class.md)<br/>
[Clase CMouseManager](reference/cmousemanager-class.md)<br/>
[Implicaciones de seguridad de la personalización](security-implications-of-customization.md)
