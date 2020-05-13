---
title: 'TN028: Compatibilidad con la ayuda contextual'
ms.date: 11/04/2016
f1_keywords:
- vc.help
helpviewer_keywords:
- context-sensitive Help [MFC], MFC applications
- TN028
- resource identifiers, context-sensitive Help
ms.assetid: 884f1c55-fa27-4d4c-984f-30907d477484
ms.openlocfilehash: 502edc837d7886dd60ab5107fb194c1490a76928
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370328"
---
# <a name="tn028-context-sensitive-help-support"></a>TN028: Compatibilidad con la ayuda contextual

Esta nota describe las reglas para asignar identificadores de contexto sin contexto de ayuda y otros problemas de ayuda en MFC. La compatibilidad con la ayuda contextual requiere el compilador de ayuda que está disponible en Visual C++.

> [!NOTE]
> Además de implementar ayuda contextual mediante WinHelp, MFC también admite el uso de la Ayuda HTML. Para obtener más información sobre esta compatibilidad y programación con la Ayuda HTML, consulte [Ayuda HTML: Ayuda contextual para sus programas](../mfc/html-help-context-sensitive-help-for-your-programs.md).

## <a name="types-of-help-supported"></a>Tipos de ayuda admitida

Hay dos tipos de ayuda contextual implementada en aplicaciones de Windows. La primera, denominada "Ayuda F1", implica iniciar WinHelp con el contexto adecuado basado en el objeto activo actualmente. El segundo es el modo "Shift+ F1". En este modo, el cursor del ratón cambia al cursor de ayuda y el usuario procede a hacer clic en un objeto. En ese momento, WinHelp se inicia para proporcionar ayuda para el objeto en el que el usuario ha iniciado clic.

Las clases de Microsoft Foundation implementan ambas formas de ayuda. Además, el marco de trabajo admite dos comandos de ayuda simples, Help Index y Using Help.

## <a name="help-files"></a>Archivos de ayuda

Las clases de Microsoft Foundation asumen un único archivo de Ayuda. Ese archivo de Ayuda debe tener el mismo nombre y ruta de acceso que la aplicación. Por ejemplo, si el archivo ejecutable es C:-MiAplicación-MiAyuda.exe el archivo de ayuda debe ser C:-MiAplicación-MiAyuda.hlp. La ruta de acceso se establece a través de la *m_pszHelpFilePath* variable miembro de la [clase CWinApp](../mfc/reference/cwinapp-class.md).

## <a name="help-context-ranges"></a>Rangos de contexto de ayuda

La implementación predeterminada de MFC requiere que un programa siga algunas reglas sobre la asignación de los guid de contexto de ayuda. Estas reglas son un rango de identificadores asignados a controles específicos. Puede invalidar estas reglas proporcionando diferentes implementaciones de las distintas funciones miembro relacionadas con la Ayuda.

```
0x00000000 - 0x0000FFFF : user defined
0x00010000 - 0x0001FFFF : commands (menus/command buttons)
0x00010000 + ID_
(note: 0x18000-> 0x1FFFF is the practical range since command IDs are>=0x8000)
0x00020000 - 0x0002FFFF : windows and dialogs
0x00020000 + IDR_
(note: 0x20000-> 0x27FFF is the practical range since IDRs are <= 0x7FFF)
0x00030000 - 0x0003FFFF : error messages (based on error string ID)
0x00030000 + IDP_
0x00040000 - 0x0004FFFF : special purpose (non-client areas)
0x00040000 + HitTest area
0x00050000 - 0x0005FFFF : controls (those that are not commands)
0x00040000 + IDW_
```

## <a name="simple-help-commands"></a>Comandos simples de "Ayuda"

Hay dos comandos de Ayuda simples implementados por Microsoft Foundation Classes:

- ID_HELP_INDEX que implementa [CWinApp::OnHelpIndex](../mfc/reference/cwinapp-class.md#onhelpindex)

- ID_HELP_USING que es implementado por [CWinApp::OnHelpUsing](../mfc/reference/cwinapp-class.md#onhelpusing)

El primer comando muestra el índice de Ayuda de la aplicación. El segundo muestra la ayuda del usuario en el uso del programa WinHelp.

## <a name="context-sensitive-help-f1-help"></a>Ayuda contextual (Ayuda de F1)

La tecla F1 normalmente se traduce a un comando con un ID de ID_HELP por un acelerador colocado en la tabla de aceleradores de la ventana principal. El comando ID_HELP también se puede generar mediante un botón con un ID de ID_HELP en la ventana principal o el cuadro de diálogo.

Independientemente de cómo se genere el comando ID_HELP, se enruta como un comando normal hasta que alcanza un controlador de comandos. Para obtener más información acerca de la arquitectura de enrutamiento de comandos MFC, consulte [la Nota técnica 21.](../mfc/tn021-command-and-message-routing.md) Si la aplicación tiene la Ayuda habilitada, [CWinApp::OnHelp](../mfc/reference/cwinapp-class.md#onhelp)controlará el comando ID_HELP. El objeto de aplicación recibe el mensaje de ayuda y, a continuación, enruta el comando de forma adecuada. Esto es necesario ya que el enrutamiento de comandos predeterminado no es adecuado para determinar el contexto más específico.

`CWinApp::OnHelp`intenta iniciar WinHelp en el siguiente orden:

1. Comprueba si hay `AfxMessageBox` una llamada activa con un identificador de ayuda. Si un cuadro de mensaje está activo actualmente, WinHelp se inicia con el contexto adecuado a ese cuadro de mensaje.

1. Envía un mensaje de WM_COMMANDHELP a la ventana activa. Si esa ventana no responde iniciando WinHelp, se envía el mismo mensaje a los antepasados de esa ventana hasta que se procesa el mensaje o la ventana actual es una ventana de nivel superior.

1. Envía un comando ID_DEFAULT_HELP a la ventana principal. Esto invoca la Ayuda predeterminada. Este comando se asocia `CWinApp::OnHelpIndex`generalmente a .

Para invalidar globalmente los valores base de ID predeterminados (por ejemplo, 0x10000 para comandos y 0x20000 para recursos como cuadros de diálogo), la aplicación debe invalidar [CWinApp::WinHelp](../mfc/reference/cwinapp-class.md#winhelp).

Para invalidar esta funcionalidad y la forma en que se determina un contexto de Ayuda, debe controlar el mensaje WM_COMMANDHELP. Es posible que desee proporcionar un enrutamiento de ayuda más específico de lo que proporciona el marco de trabajo, ya que solo va tan profundo como la ventana secundaria MDI actual. También puede proporcionar ayuda más específica para una ventana o cuadro de diálogo determinado, tal vez en función del estado interno actual de ese objeto o el control activo dentro del cuadro de diálogo.

## <a name="wm_commandhelp"></a>WM_COMMANDHELP

```

afx_msg LRESULT CWnd::OnCommandHelp(WPARAM wParam, LPARAM lParam)
```

WM_COMMANDHELP es un mensaje privado de Windows MFC que recibe la ventana activa cuando se solicita la Ayuda. Cuando la ventana recibe este mensaje, puede llamar `CWinApp::WinHelp` con contexto que coincida con el estado interno de la ventana.

*lParam*<br/>
Contiene el contexto de Ayuda disponible actualmente. *lParam* es cero si no se ha determinado ningún contexto de Ayuda. Una implementación de puede usar el identificador de `OnCommandHelp` contexto en *lParam* para determinar un contexto diferente o simplemente puede pasarlo a `CWinApp::WinHelp`.

*wParam*<br/>
No se utiliza y será cero.

Si `OnCommandHelp` la `CWinApp::WinHelp`función llama , debe devolver **TRUE**. Devolver **TRUE** detiene el enrutamiento de este comando a otras clases y a otras ventanas.

## <a name="help-mode-shiftf1-help"></a>Modo de ayuda (Ayuda de Mayús+F1)

Esta es la segunda forma de Ayuda contextual. Por lo general, este modo se introduce pulsando SHIFT+F1 o a través del menú/barra de herramientas. Se implementa como un comando (ID_CONTEXT_HELP). El enlace de filtro de mensajes no se utiliza para traducir este comando mientras un cuadro de diálogo modal o`CWinApp::Run`menú está activo, por lo tanto, este comando sólo está disponible para el usuario cuando la aplicación está ejecutando la bomba de mensajes principal ( ).

Después de entrar en este modo, el cursor del ratón de Ayuda se muestra en todas las áreas de la aplicación, incluso si la aplicación normalmente mostraría su propio cursor para esa área (como el borde de tamaño alrededor de la ventana). El usuario puede utilizar el ratón o el teclado para seleccionar un comando. En lugar de ejecutar el comando, se muestra la Ayuda en ese comando. Además, el usuario puede hacer clic en un objeto visible en la pantalla, como un botón en la barra de herramientas, y se mostrará la Ayuda para ese objeto. Este modo de Ayuda `CWinApp::OnContextHelp`es proporcionado por .

Durante la ejecución de este bucle, todas las entradas del teclado están inactivas, excepto las teclas que acceden al menú. Además, la traducción `PreTranslateMessage` de comandos todavía se realiza a través de permitir que el usuario presione una tecla aceleradora y reciba ayuda en ese comando.

Si hay traducciones o acciones particulares que tienen lugar en la `PreTranslateMessage` función que no deberíatener durante el modo de ayuda SHIFT+F1, debe comprobar el *m_bHelpMode* miembro antes `CWinApp` de realizar esas operaciones. La `CDialog` implementación de `PreTranslateMessage` comprobaciones esto antes de llamar a `IsDialogMessage`, por ejemplo. Esto deshabilita las teclas de "navegación de diálogo" en los cuadros de diálogo no moderes durante el modo SHIFT+F1. Además, `CWinApp::OnIdle` todavía se llama durante este bucle.

Si el usuario elige un comando del menú, se maneja como ayuda en ese comando (a través de WM_COMMANDHELP, consulte a continuación). Si el usuario hace clic en un área visible de la ventana de aplicaciones, se determina si se trata de un clic no cliente o un clic de cliente. `OnContextHelp`controla automáticamente la asignación de clics no cliente a clics de cliente. Si es un clic de cliente, envía un WM_HELPHITTEST a la ventana en la que se hizo clic. Si esa ventana devuelve un valor distinto de cero, ese valor se utiliza como contexto de ayuda. Si devuelve cero, `OnContextHelp` intenta la ventana primaria (y en su defecto, su elemento primario, etc.). Si no se puede determinar un contexto de Ayuda, el valor predeterminado es enviar `CWinApp::OnHelpIndex`un comando ID_DEFAULT_HELP a la ventana principal, que, a continuación, (normalmente) se asigna a .

## <a name="wm_helphittest"></a>WM_HELPHITTEST

```

afx_msg LRESULT CWnd::OnHelpHitTest(
WPARAM, LPARAM lParam)
```

WM_HELPHITTEST es un mensaje de ventanas privadas MFC que recibe la ventana activa pulsada durante el modo de Ayuda SHIFT+F1. Cuando la ventana recibe este mensaje, devuelve un identificador de ayuda **DWORD** para su uso por WinHelp.

LOWORD(lParam) contiene la coordenada del dispositivo del eje X donde se hizo clic en el mouse en relación con el área de cliente de la ventana.

HIWORD(lParam) contiene la coordenada del eje Y.

*wParam*<br/>
no se utiliza y será cero. Si el valor devuelto es distinto de cero, winHelp se llama con ese contexto. Si el valor devuelto es cero, se consulta la ventana primaria para obtener ayuda.

En muchos casos, puede aprovechar el código de prueba de posicionamiento que ya puede tener. Vea la `CToolBar::OnHelpHitTest` implementación de para obtener un ejemplo de control del mensaje WM_HELPHITTEST (el `CControlBar`código aprovecha el código de prueba de posicionamiento utilizado en botones y información sobre herramientas en ).

## <a name="mfc-application-wizard-support-and-makehm"></a>Compatibilidad con el Asistente para aplicaciones MFC y MAKEHM

El Asistente para aplicaciones MFC crea los archivos necesarios para compilar un archivo de Ayuda (archivos .cnt y .hpj). También incluye una serie de archivos .rtf precompilados que son aceptados por el compilador de Ayuda de Microsoft. Muchos de los temas están completos, pero algunos pueden necesitar ser modificados para su aplicación específica.

La creación automática de un archivo de "asignación de ayuda" es compatible con una utilidad llamada MAKEHM. La utilidad MAKEHM puede traducir el RESOURCE de una aplicación. H a un archivo de asignación de ayuda. Por ejemplo:

```
#define IDD_MY_DIALOG   2000
#define ID_MY_COMMAND   150
```

se traducirá en:

```
HIDD_MY_DIALOG    0x207d0
HID_MY_COMMAND    0x10096
```

Este formato es compatible con las instalaciones del compilador de ayuda, que asigna identificadores de contexto (los números en el lado derecho) con nombres de tema (los símbolos en el lado izquierdo).

El código fuente de MAKEHM está disponible en el ejemplo DE utilidades de programación de MFC [MAKEHM](../overview/visual-cpp-samples.md).

## <a name="adding-help-support-after-running-the-mfc-application-wizard"></a>Agregar compatibilidad con ayuda después de ejecutar el Asistente para aplicaciones MFC

La mejor manera de agregar ayuda a la aplicación es comprobar la opción "Ayuda contextual" en la página Características avanzadas del Asistente para aplicaciones MFC antes de crear la aplicación. De este modo, el Asistente para aplicaciones MFC `CWinApp`agrega automáticamente las entradas de mapa de mensajes necesarias a la clase derivada para admitir la Ayuda.

## <a name="help-on-message-boxes"></a>Ayuda en cuadros de mensajes

La Ayuda en cuadros de mensaje `AfxMessageBox` (a veces `MessageBox` denominadas alertas) se admite a través de la función, un contenedor para la API de Windows.

Hay dos versiones de `AfxMessageBox`, una para su uso con un`LPCSTR`id de cadena y otra para su uso con un puntero a la cadena ( ):

```
int AFXAPI AfxMessageBox(LPCSTR lpszText,
    UINT nType,
    UINT nIDHelp);

int AFXAPI AfxMessageBox(UINT nIDPrompt,
    UINT nType,
    UINT nIDHelp);
```

En ambos casos, hay un identificador de ayuda opcional.

En el primer caso, el valor predeterminado para nIDHelp es 0, lo que indica que no hay ayuda para este cuadro de mensaje. Si el usuario presiona F1 mientras el cuadro de mensaje está activo, el usuario no recibirá Ayuda (incluso si la aplicación admite Ayuda). Si esto no es deseable, se debe proporcionar un identificador de ayuda para nIDHelp.

En el segundo caso, el valor predeterminado de nIDHelp es -1, lo que indica que el identificador de ayuda es el mismo que nIDPrompt. La ayuda solo funcionará si la aplicación está habilitada para la Ayuda, por supuesto). Debe proporcionar 0 para nIDHelp si desea que el cuadro de mensaje no tenga soporte de ayuda. Si desea que el mensaje esté habilitado para la Ayuda, pero desea un identificador de ayuda diferente que nIDPrompt, simplemente proporcione un valor positivo para nIDHelp diferente del de nIDPrompt.

## <a name="see-also"></a>Consulte también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)
