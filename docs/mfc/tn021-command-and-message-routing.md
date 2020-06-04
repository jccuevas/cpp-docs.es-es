---
title: 'TN021: Enrutamiento de comandos y mensajes'
ms.date: 06/28/2018
f1_keywords:
- vc.routing
helpviewer_keywords:
- TN021
- command routing [MFC], technical note TN021
- Windows messages [MFC], routing
ms.assetid: b5952c8b-123e-406c-a36d-a6ac7c6df307
ms.openlocfilehash: bdd405bda5c0af9e04a50eee4ef5738f3a53259e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370407"
---
# <a name="tn021-command-and-message-routing"></a>TN021: Enrutamiento de comandos y mensajes

> [!NOTE]
> La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea. Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos. Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.

Esta nota describe la arquitectura de enrutamiento y envío de comandos, así como temas avanzados en el enrutamiento de mensajes de ventana general.

Consulte Visual C++ para obtener detalles generales sobre las arquitecturas descritas aquí, especialmente la distinción entre los mensajes de Windows, las notificaciones de control y los comandos. En esta nota se supone que está muy familiarizado con los problemas descritos en la documentación impresa y solo aborda temas muy avanzados.

## <a name="command-routing-and-dispatch-mfc-10-functionality-evolves-to-mfc-20-architecture"></a>La funcionalidad de enrutamiento y distribución de MFC 1.0 evoluciona a la arquitectura MFC 2.0

Windows tiene el WM_COMMAND mensaje que está sobrecargado para proporcionar notificaciones de comandos de menú, teclas de aceleración y notificaciones de control de cuadro de diálogo.

MFC 1.0 basado en eso un poco al permitir que un controlador `CWnd` de comandos (por ejemplo, "OnFileNew") en una clase derivada para ser llamado en respuesta a un WM_COMMAND específico. Esto se pega junto con una estructura de datos denominada mapa de mensajes y da como resultado un mecanismo de comando muy eficiente en el espacio.

MFC 1.0 también proporciona funcionalidad adicional para separar las notificaciones de control de los mensajes de comando. Los comandos se representan mediante un identificador de 16 bits, a veces conocido como identificador de comando. Los comandos `CFrameWnd` normalmente comienzan desde un (es decir, una selección de menú o un acelerador traducido) y se enrutan a una variedad de otras ventanas.

MFC 1.0 utiliza el enrutamiento de comandos en un sentido limitado para la implementación de la interfaz de documento múltiple (MDI). (Un comando de delegado de ventana de marco MDI a su ventana secundaria MDI activa.)

Esta funcionalidad se ha generalizado y ampliado en MFC 2.0 para permitir que los comandos se controlen mediante un rango más amplio de objetos (no solo objetos de ventana). Proporciona una arquitectura más formal y extensible para enrutar mensajes y reutiliza el enrutamiento de destino de comandos no solo para controlar comandos, sino también para actualizar objetos de interfaz de usuario (como elementos de menú y botones de barra de herramientas) para reflejar la disponibilidad actual de un comando.

## <a name="command-ids"></a>Identificadores de comando

Consulte Visual C++ para obtener una explicación del proceso de enrutamiento y enlace de comandos. [La Nota técnica 20](../mfc/tn020-id-naming-and-numbering-conventions.md) contiene información sobre la nomenclatura de ID.

Usamos el prefijo genérico "ID_" para los argumentos de comando. Los ID de comando se >0x8000. La línea de mensaje o la barra de estado mostrará la cadena de descripción del comando si hay un recurso STRINGTABLE con los mismos identificadores que el identificador de comando.

En los recursos de la aplicación, puede aparecer un identificador de comando en varios lugares:

- En un recurso STRINGTABLE que tiene el mismo identificador que el símbolo del sistema de la línea de mensajes.

- En posiblemente muchos recursos MENU que están asociados a elementos de menú que invocan el mismo comando.

- (AVANZADO) en un botón de diálogo para un comando GOSUB.

En el código fuente de la aplicación, puede aparecer un identificador de comando en varios lugares:

- En su RECURSO. H (u otro archivo de encabezado de símbolo principal) para definir identificadores de comando específicos de la aplicación.

- PERHAPS En una matriz de ID utilizada para crear una barra de herramientas.

- En una macro ON_COMMAND.

- TAL VEZ en una macro ON_UPDATE_COMMAND_UI.

Actualmente, la única implementación en MFC que requiere que los ID de comando se >0x8000 es la implementación de los cuadros de diálogo/comandos de GOSUB.

## <a name="gosub-commands-using-command-architecture-in-dialogs"></a>Comandos GOSUB, uso de la arquitectura de comandos en los cuadros de diálogo

La arquitectura de comandos de enrutamiento y habilitación de comandos funciona bien con ventanas de marco, elementos de menú, botones de barra de herramientas, botones de barra de diálogo, otras barras de control y otros elementos de la interfaz de usuario diseñados para actualizar a petición y enrutar comandos o controlar ID a un destino de comando principal (normalmente la ventana de marco principal). Ese destino de comando principal puede enrutar las notificaciones de comando o control a otros objetos de destino de comando según corresponda.

Un cuadro de diálogo (modal o no modal) puede beneficiarse de algunas de las características de la arquitectura de comandos si asigna el identificador de control del control de cuadro de diálogo al identificador de comando adecuado. La compatibilidad con los cuadros de diálogo no es automática, por lo que es posible que tenga que escribir código adicional.

Tenga en cuenta que para que todas estas características funcionen correctamente, los ID de comando deben estar >0x8000. Puesto que muchos cuadros de diálogo podrían enrutarse al mismo marco, los comandos compartidos deben ser >0x8000, mientras que los IDC no compartidos en un cuadro de diálogo específico deben estar <a 0x7FFF.

Puede colocar un botón normal en un cuadro de diálogo modal normal con el IDC del botón establecido en el identificador de comando adecuado. Cuando el usuario selecciona el botón, el propietario del cuadro de diálogo (normalmente la ventana de marco principal) obtiene el comando como cualquier otro comando. Esto se denomina comando GOSUB, ya que normalmente se utiliza para abrir otro cuadro de diálogo (un GOSUB del primer cuadro de diálogo).

También puede llamar `CWnd::UpdateDialogControls` a la función en el cuadro de diálogo y pasarle la dirección de la ventana de marco principal. Esta función habilitará o deshabilitará los controles de cuadro de diálogo en función de si tienen controladores de comandos en el marco. Esta función se llama automáticamente para las barras de control en el bucle inactivo de la aplicación, pero debe llamarla directamente para los cuadros de diálogo normales que desea que tenga esta característica.

## <a name="when-on_update_command_ui-is-called"></a>Cuando se llama a ON_UPDATE_COMMAND_UI

Mantener el estado habilitado/comprobado de todos los elementos de menú de un programa todo el tiempo puede ser un problema computacionalmente costoso. Una técnica común es habilitar/comprobar elementos de menú solo cuando el usuario selecciona el POPUP. La implementación de `CFrameWnd` MFC 2.0 controla el mensaje WM_INITMENUPOPUP y usa la arquitectura de enrutamiento de comandos para determinar los estados de los menús a través de controladores de ON_UPDATE_COMMAND_UI.

`CFrameWnd`También controla el mensaje WM_ENTERIDLE para describir el elemento de menú actual seleccionado en la barra de estado (también conocida como línea de mensaje).

La estructura de menús de una aplicación, editada por Visual C++, se utiliza para representar los comandos potenciales disponibles en WM_INITMENUPOPUP momento. ON_UPDATE_COMMAND_UI controladores pueden modificar el estado o el texto de un menú, o para usos avanzados (como la lista MRU de archivo o el menú emergente Verbos OLE), en realidad modificar la estructura del menú antes de dibujar el menú.

El mismo tipo de procesamiento ON_UPDATE_COMMAND_UI se realiza para las barras de herramientas (y otras barras de control) cuando la aplicación entra en su bucle inactivo. Consulte la Referencia de la biblioteca de *clases* y la [Nota técnica 31](../mfc/tn031-control-bars.md) para obtener más información sobre las barras de control.

## <a name="nested-pop-up-menus"></a>Menús emergentes anidados

Si utiliza una estructura de menú anidada, observará que el controlador de ON_UPDATE_COMMAND_UI para el primer elemento de menú en el menú emergente se llama en dos casos diferentes.

En primer lugar, se llama para el propio menú emergente. Esto es necesario porque los menús emergentes no tienen ID y usamos el ID del primer elemento de menú del menú emergente para hacer referencia a todo el menú emergente. En este caso, la variable `CCmdUI` miembro *m_pSubMenu* del objeto no será NULL y apuntará al menú emergente.

En segundo lugar, se llama justo antes de que se dibujen los elementos de menú en el menú emergente. En este caso, el identificador hace referencia *m_pSubMenu* solo al primer `CCmdUI` elemento de menú y la variable miembro m_pSubMenu del objeto será NULL.

Esto le permite habilitar el menú emergente distinto de sus elementos de menú, pero requiere que escriba algún código que tenga en cuenta el menú. Por ejemplo, en un menú anidado con la siguiente estructura:

```Output
File>
    New>
    Sheet (ID_NEW_SHEET)
    Chart (ID_NEW_CHART)
```

Los comandos ID_NEW_SHEET y ID_NEW_CHART se pueden habilitar o deshabilitar de forma independiente. El menú emergente **Nuevo** debe estar habilitado si alguno de los dos está habilitado.

El controlador de comandos para ID_NEW_SHEET (el primer comando en la ventana emergente) tendría un aspecto similar a:

```cpp
void CMyApp::OnUpdateNewSheet(CCmdUI* pCmdUI)
{
    if (pCmdUI->m_pSubMenu != NULL)
    {
        // enable entire pop-up for "New" sheet and chart
        BOOL bEnable = m_bCanCreateSheet || m_bCanCreateChart;
        // CCmdUI::Enable is a no-op for this case, so we
        // must do what it would have done.
        pCmdUI->m_pMenu->EnableMenuItem(pCmdUI->m_nIndex,
            MF_BYPOSITION |
            (bEnable  MF_ENABLED : (MF_DISABLED | MF_GRAYED)));

        return;
    }
    // otherwise just the New Sheet command
    pCmdUI->Enable(m_bCanCreateSheet);
}
```

El controlador de comandos para ID_NEW_CHART sería un controlador de comandos de actualización normal y tendría un aspecto similar a:

```cpp
void CMyApp::OnUpdateNewChart(CCmdUI* pCmdUI)
{
    pCmdUI->Enable(m_bCanCreateChart);
}
```

## <a name="on_command-and-on_bn_clicked"></a>ON_COMMAND y ON_BN_CLICKED

Las macros de mapa de mensajes para **ON_COMMAND** y **ON_BN_CLICKED** son las mismas. El mecanismo de enrutamiento de notificaciones de control y comandoMFC solo utiliza el identificador de comando para decidir a dónde enrutar. Las notificaciones de control con código de notificación de control de cero (**BN_CLICKED**) se interpretan como comandos.

> [!NOTE]
> De hecho, todos los mensajes de notificación de control pasan por la cadena del controlador de comandos. Por ejemplo, es técnicamente posible escribir un controlador de notificación de control para **EN_CHANGE** en la clase de documento. Esto no es generalmente recomendable porque las aplicaciones prácticas de esta característica son pocas, la característica no es compatible con ClassWizard, y el uso de la característica puede dar lugar a código frágil.

## <a name="disabling-the-automatic-disabling-of-button-controls"></a>Deshabilitar la desactivación automática de los controles de botón

Si coloca un control de botón en una barra de diálogo, o en un cuadro de diálogo con el que llama a **CWnd::UpdateDialogControls** por su cuenta, observará que los botones que no tienen **ON_COMMAND** o **controladores de ON_UPDATE_COMMAND_UI** se deshabilitarán automáticamente por el marco de trabajo. En algunos casos, no necesitará tener un controlador, pero deseará que el botón permanezca habilitado. La forma más fácil de lograr esto es agregar un controlador de comandos ficticio (fácil de hacer con ClassWizard) y no hacer nada en él.

## <a name="window-message-routing"></a>Enrutamiento de mensajes de ventana

A continuación se describen algunos temas más avanzados sobre las clases MFC y cómo les afectan el enrutamiento de mensajes de Windows y otros temas. La información aquí sólo se describe brevemente. Consulte la Referencia de la biblioteca de *clases* para obtener más información sobre las API públicas. Consulte el código fuente de la biblioteca MFC para obtener más información sobre los detalles de implementación.

Consulte [la Nota técnica 17](../mfc/tn017-destroying-window-objects.md) para obtener más información sobre la limpieza de ventanas, un tema muy importante para todas las clases derivadas de **CWnd.**

## <a name="cwnd-issues"></a>Problemas con CWnd

La función miembro de implementación **CWnd::OnChildNotify** proporciona una arquitectura eficaz y extensible para ventanas secundarias (también conocidas como controles) para enlazar o de otro modo ser informado de mensajes, comandos y notificaciones de control que van a su elemento primario (o "propietario"). Si la ventana secundaria (/control) es un C++ **CWnd** propio objeto, la función virtual **OnChildNotify** se llama primero con los parámetros del mensaje original (es decir, una estructura **MSG).** La ventana secundaria puede dejar el mensaje solo, comerlo o modificar el mensaje para el padre (poco frecuente).

La implementación predeterminada de **CWnd** controla los siguientes mensajes y utiliza el enlace **OnChildNotify** para permitir que las ventanas secundarias (controles) accedan primero al mensaje:

- **WM_MEASUREITEM** y **WM_DRAWITEM** (para autodibujo)

- **WM_COMPAREITEM** y **WM_DELETEITEM** (para autodibujo)

- **WM_HSCROLL** y **WM_VSCROLL**

- **WM_CTLCOLOR**

- **WM_PARENTNOTIFY**

Observará que el enlace **OnChildNotify** se utiliza para cambiar los mensajes dibujados por el propietario en mensajes auto-dibujo.

Además del enlace **OnChildNotify,** los mensajes de desplazamiento tienen un comportamiento de enrutamiento adicional. Consulte a continuación para obtener más detalles sobre las barras de desplazamiento y fuentes de **WM_HSCROLL** y **mensajes WM_VSCROLL.**

## <a name="cframewnd-issues"></a>Problemas de CFrameWnd

La clase **CFrameWnd** proporciona la mayor parte del enrutamiento de comandos y la implementación de actualización de la interfaz de usuario. Esto se utiliza principalmente para la ventana de marco principal de la aplicación (**CWinApp::m_pMainWnd**) pero se aplica a todas las ventanas de marco.

La ventana de marco principal es la ventana con la barra de menús y es el elemento primario de la barra de estado o la línea de mensaje. Refiera por favor a la discusión antedicha sobre el ruteo de comandos y **WM_INITMENUPOPUP.**

La clase **CFrameWnd** proporciona administración de la vista activa. Los siguientes mensajes se enrutan a través de la vista activa:

- Todos los mensajes de comando (la vista activa obtiene el primer acceso a ellos).

- **WM_HSCROLL** y **WM_VSCROLL** mensajes de las barras de desplazamiento del mismo vista (ver más abajo).

- **WM_ACTIVATE** (y **WM_MDIACTIVATE** para MDI) se convierten en llamadas a la función virtual **CView::OnActivateView**.

## <a name="cmdiframewndcmdichildwnd-issues"></a>Problemas de CMDIFrameWnd/CMDIChildWnd

Ambas clases de ventana de marco MDI derivan de **CFrameWnd** y, por lo tanto, están habilitadas para el mismo tipo de enrutamiento de comandos y actualización de la interfaz de usuario proporcionada en **CFrameWnd**. En una aplicación MDI típica, solo la ventana de marco principal (es decir, el objeto **CMDIFrameWnd)** contiene la barra de menús y la barra de estado y, por lo tanto, es el origen principal de la implementación de enrutamiento de comandos.

El esquema de enrutamiento general es que la ventana secundaria MDI activa obtiene el primer acceso a los comandos. Las funciones **PreTranslateMessage** predeterminadas controlan las tablas de aceleradores para las ventanas secundarias MDI (primero) y el marco MDI (segundo), así como los aceleradores de comandos de sistema MDI estándar normalmente controlados por **TranslateMDISysAccel** (último).

## <a name="scroll-bar-issues"></a>Problemas de la barra de desplazamiento

Al controlar el mensaje de desplazamiento **(WM_HSCROLL**/**OnHScroll** y/o **WM_VSCROLL**/**OnVScroll**), debe intentar escribir el código del controlador para que no se base en la procedeción del mensaje de la barra de desplazamiento. Esto no es sólo un problema general de Windows, ya que los mensajes de desplazamiento pueden provenir de controles de barra de desplazamiento verdaderos o de **WS_HSCROLL**/**WS_VSCROLL** barras de desplazamiento que no son controles de barra de desplazamiento.

MFC extiende eso para permitir que los controles de barra de desplazamiento sean secundarios o hermanos de la ventana que se está desplazando (de hecho, la relación primario/secundario entre la barra de desplazamiento y la ventana que se está desplazando puede ser cualquier cosa). Esto es especialmente importante para las barras de desplazamiento compartidas con ventanas divisoras. Consulte [la Nota técnica 29](../mfc/tn029-splitter-windows.md) para obtener más información sobre la implementación de **CSplitterWnd,** incluida más información sobre los problemas de la barra de desplazamiento compartida.

En una nota lateral, hay dos clases derivadas **de CWnd** donde los estilos de barra de desplazamiento especificados en el momento de creación se quedan atrapados y no se pasan a Windows. Cuando se pasa a una rutina de creación, **WS_HSCROLL** y **WS_VSCROLL** se pueden establecer de forma independiente, pero después de la creación no se puede cambiar. Por supuesto, no debe probar o establecer directamente los bits de estilo WS_SCROLL de la ventana que crearon.

Para **CMDIFrameWnd** los estilos de barra de desplazamiento que se pasan a **Crear** o **LoadFrame** se utilizan para crear el MDICLIENT. Si desea tener un área MDICLIENT desplazable (como el Administrador de programas de Windows), asegúrese de establecer ambos estilos de barra de desplazamiento **(WS_HSCROLL** &#124; **WS_VSCROLL**) para el estilo utilizado para crear **CMDIFrameWnd**.

Para **CSplitterWnd** los estilos de barra de desplazamiento se aplican a las barras de desplazamiento compartidas especiales para las regiones divisoras. Para las ventanas divisoras estáticas, normalmente no establecerá ningún estilo de barra de desplazamiento. Para las ventanas divisoras dinámicas, normalmente tendrá el estilo de barra de desplazamiento establecido para la dirección que dividirá, es decir, **WS_HSCROLL** si puede dividir filas, **WS_VSCROLL** si puede dividir columnas.

## <a name="see-also"></a>Consulte también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)
