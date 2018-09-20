---
title: Personalización del teclado y Mouse | Microsoft Docs
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
ms.openlocfilehash: ba05ddfd7f3b709813a6e5069d98277c6c0baa46
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46402699"
---
# <a name="keyboard-and-mouse-customization"></a>Personalización del teclado y del mouse

MFC permite al usuario de la aplicación para personalizar cómo controla el teclado y mouse de entrada. El usuario puede personalizar la entrada de teclado mediante la asignación de métodos abreviados de teclado para comandos. El usuario también puede personalizar la entrada del mouse, seleccione el comando que se debe ejecutar cuando el usuario hace doble clic dentro de windows específicos de la aplicación. En este tema se explica cómo personalizar la entrada de la aplicación.

En el **personalización** cuadro de diálogo, el usuario puede cambiar los controles personalizados para el mouse y el teclado. Para mostrar este cuadro de diálogo, el usuario señala **personalizar** en el **vista** menú y, a continuación, hace clic en **acoplamiento y barras de herramientas**. En el cuadro de diálogo, el usuario hace clic en el **teclado** ficha o el **Mouse** ficha.

## <a name="keyboard-customization"></a>Personalización del teclado

La siguiente ilustración muestra el **teclado** pestaña de la **personalización** cuadro de diálogo.

![Pestaña teclado del cuadro de diálogo Personalizar](../mfc/media/mfcnextkeyboardtab.png "mfcnextkeyboardtab") teclado en la ficha personalización

El usuario interactúa con la pestaña de teclado para asignar uno o más métodos abreviados de teclado a un comando. Los comandos disponibles se muestran en el lado izquierdo de la pestaña. El usuario puede seleccionar cualquier comando disponible en el menú. Comandos de menú sólo pueden asociarse con un método abreviado de teclado. Cuando el usuario introduce un nuevo acceso directo, el **asignar** se habilita el botón. Cuando el usuario hace clic en este botón, la aplicación asocia el comando seleccionado a ese método abreviado.

Todos los métodos abreviados de teclado asignados actualmente aparecen en el cuadro de lista en la columna derecha. El usuario también puede seleccionar los accesos directos individuales y quitarlos o restablecer todas las asignaciones para la aplicación.

Si desea admitir esta personalización en la aplicación, debe crear un [CKeyboardManager](../mfc/reference/ckeyboardmanager-class.md) objeto. Para crear un `CKeyboardManager` de objeto, llame a la función [CWinAppEx::InitKeyboardManager](../mfc/reference/cwinappex-class.md#initkeyboardmanager). Este método crea e Inicializa un administrador de teclado. Si creas un teclado manager manualmente, todavía debe llamar a `CWinAppEx::InitKeyboardManager` para inicializarlo.

Si utiliza al Asistente para crear la aplicación, el Asistente inicializará el Administrador de teclado. Después de la aplicación inicializa el Administrador de teclado, el marco de trabajo agrega un **teclado** tabulador para ir a la **personalización** cuadro de diálogo.

## <a name="mouse-customization"></a>Personalización del mouse

La siguiente ilustración muestra el **Mouse** pestaña de la **personalización** cuadro de diálogo.

![Pestaña mouse del cuadro de diálogo Personalizar](../mfc/media/mfcnextmousetab.png "mfcnextmousetab") ficha personalización de Mouse

El usuario interactúa con esta pestaña para asignar un menú de comandos para el mouse, haga doble clic en acción. El usuario selecciona una vista del lado izquierdo de la ventana y, a continuación, utiliza los controles en el lado derecho para asociar un comando a la acción de doble clic. Después de que el usuario hace clic en **cerrar**, la aplicación ejecuta el comando asociado cada vez que el usuario hace doble clic en cualquier lugar en la vista.

De forma predeterminada, personalización del mouse no está habilitada al crear una aplicación mediante el asistente.

#### <a name="to-enable-mouse-customization"></a>Para habilitar la personalización del mouse

1. Inicializar un [CMouseManager](../mfc/reference/cmousemanager-class.md) objeto mediante una llamada a [CWinAppEx::InitMouseManager](../mfc/reference/cwinappex-class.md#initmousemanager).

1. Obtener un puntero al administrador del mouse mediante [CWinAppEx::GetMouseManager](../mfc/reference/cwinappex-class.md#getmousemanager).

1. Agregar vistas al administrador del mouse mediante el [CMouseManager::AddView](../mfc/reference/cmousemanager-class.md#addview) método. Haga esto para cada vista que desea agregar al administrador del mouse.

Después de la aplicación inicializa el administrador del mouse, el marco de trabajo agrega los **Mouse** tabulador para ir a la **personalizar** cuadro de diálogo. Si no agrega todas las vistas, obtener acceso a la pestaña provocará una excepción no controlada. Después de haber creado una lista de vistas, el **Mouse** pestaña está disponible para el usuario.

Cuando se agrega una nueva vista en el administrador del mouse, se le asigna un identificador único. Si desea admitir la personalización de mouse para una ventana, debe procesar el mensaje WM_LBUTTONDBLCLICK y llamar a la [CWinAppEx::OnViewDoubleClick](../mfc/reference/cwinappex-class.md#onviewdoubleclick) función. Cuando se llama a esta función, uno de los parámetros es el identificador de esa ventana. Es responsabilidad del programador para realizar un seguimiento de los números de identificador y los objetos asociados con ellos.

## <a name="security-concerns"></a>Cuestiones de seguridad

Como se describe en [herramientas definidas por el usuario](../mfc/user-defined-tools.md), el usuario puede asociar un identificador de herramienta definido por el usuario con el evento de doble clic. Cuando el usuario hace doble clic en una vista, la aplicación busca una herramienta de usuario que coincida con el identificador asociado. Si la aplicación encuentra una herramienta de búsqueda de coincidencias, ejecuta la herramienta. Si la aplicación no encuentra una herramienta de búsqueda de coincidencias, envía un mensaje WM_COMMAND con el identificador a la vista que se hizo doble clic.

La configuración personalizada se almacena en el registro. Si modifica el registro, un atacante puede reemplazar un identificador de la herramienta de usuario válido con un comando arbitrario. Cuando el usuario hace doble clic en una vista, la vista procesa el comando que el atacante plantado. Esto podría provocar un comportamiento inesperado y potencialmente peligroso.

Además, este tipo de ataque puede eludir las medidas de seguridad de interfaz de usuario. Por ejemplo, suponga que una aplicación tiene deshabilitada la impresión. Es decir, en su interfaz de usuario, el **impresión** menú y el botón no están disponibles. Normalmente esto impide que la aplicación de impresión. Pero si un atacante puede editar el registro, un usuario puede ahora podría enviar el comando de impresión directamente haciendo doble clic en la vista, omitiendo los elementos de interfaz de usuario que no están disponibles.

Para protegerse contra este tipo de ataque, agregue código al controlador de comando de aplicación para comprobar que un comando es válido antes de ejecutarlo. No dependen de la interfaz de usuario para impedir que un comando que se envían a la aplicación.

## <a name="see-also"></a>Vea también

[Personalización de MFC](../mfc/customization-for-mfc.md)<br/>
[CKeyboardManager (clase)](../mfc/reference/ckeyboardmanager-class.md)<br/>
[CMouseManager (clase)](../mfc/reference/cmousemanager-class.md)<br/>
[Implicaciones de seguridad de la personalización](../mfc/security-implications-of-customization.md)

