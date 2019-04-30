---
title: 'TN021: Comando y el enrutamiento de mensajes'
ms.date: 06/28/2018
f1_keywords:
- vc.routing
helpviewer_keywords:
- TN021
- command routing [MFC], technical note TN021
- Windows messages [MFC], routing
ms.assetid: b5952c8b-123e-406c-a36d-a6ac7c6df307
ms.openlocfilehash: ce8aa2013c8f2f351ca1028f0d6103135ba5ecd8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62306186"
---
# <a name="tn021-command-and-message-routing"></a>TN021: Comando y el enrutamiento de mensajes

> [!NOTE]
>  La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea. Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos. Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.

Esta nota describe la arquitectura de comandos de enrutamiento y distribución, así como temas avanzados de enrutamiento de mensajes de ventana general.

Consulte Visual C++ para obtener información general sobre las arquitecturas que se describen aquí, especialmente la distinción entre los mensajes, las notificaciones de control y los comandos de Windows. Esta nota se supone que está muy familiarizado con los problemas descritos en la documentación impresa y sólo trata los temas muy avanzados.

## <a name="command-routing-and-dispatch-mfc-10-functionality-evolves-to-mfc-20-architecture"></a>Funcionalidad de envío y enrutamiento de comandos MFC 1.0 evoluciona a MFC 2.0 arquitectura

Windows tiene el mensaje WM_COMMAND que se sobrecarga para proporcionar notificaciones sobre los comandos de menú, teclas de aceleración y notificaciones del control de cuadro de diálogo.

MFC 1.0 basado en que un poco al permitir que un controlador de comandos (por ejemplo, "OnFileNew") un `CWnd` clase sea llamado en respuesta a WM_COMMAND específica derivada. Esto se pega junto con una estructura de datos denominada el mapa de mensajes y da como resultado un mecanismo muy eficaz del espacio del comando.

MFC 1.0 también proporcionan una funcionalidad adicional para separar las notificaciones de control de mensajes de comando. Los comandos se representan mediante un Id. de 16 bits, a veces se conoce como un identificador de comando. Comandos inician normalmente desde un `CFrameWnd` (es decir, un menú, seleccione o un acelerador traducido) y se enrutan a una variedad de otras ventanas.

MFC 1.0 utiliza enrutamiento de comandos en un sentido limitado para la implementación de interfaz de múltiples documentos (MDI). (Una ventana marco MDI delegar comandos a su ventana secundaria MDI activa).

Esta funcionalidad se ha generalizado y ampliado en MFC 2.0 para permitir los comandos que va a administrar una amplia variedad de objetos (no solo los objetos de ventana). Proporciona más formal y arquitectura extensible para el enrutamiento de mensajes y vuelve a usar el enrutamiento de destino de comando para controlar no sólo de comandos, sino también para actualizar objetos de interfaz de usuario (por ejemplo, los elementos de menú y botones de barra de herramientas) para reflejar la disponibilidad actual de un comando .

## <a name="command-ids"></a>Identificadores de comando

Vea Visual C++ para obtener una explicación del comando enrutamiento y el proceso de enlace. [Nota técnica 20](../mfc/tn020-id-naming-and-numbering-conventions.md) contiene información sobre los nombres de identificador.

Usamos el prefijo "ID_" genérico para los identificadores de comando. Los identificadores de comando son > = 0 x 8000. La barra de estado o la línea de mensaje mostrará la cadena de descripción de comandos si hay un recurso STRINGTABLE con los mismos identificadores como el identificador de comando.

En los recursos de la aplicación, un comando que puede identificador aparece en varios lugares:

- En un recurso STRINGTABLE tiene el mismo identificador que el símbolo del sistema de línea de mensaje.

- En posiblemente muchos recursos de menú que están asociados a elementos de menú que invocan el mismo comando.

- (Avanzado) en un botón de cuadro de diálogo para un comando GOSUB.

En el código fuente de la aplicación, un comando que puede identificador aparece en varios lugares:

- En el recurso. H (u otro archivo de encabezado de símbolos principal) para definir los identificadores de comandos específicos de la aplicación.

- Por ejemplo, en una matriz de Id. utilizada para crear una barra de herramientas.

- En un ON_COMMAND (macro).

- QUIZÁS en un ON_UPDATE_COMMAND_UI (macro).

Actualmente, la única implementación de MFC que requiere que los identificadores de comando ser > = 0 x 8000 es la implementación de GOSUB cuadros de diálogo y comandos.

## <a name="gosub-commands-using-command-architecture-in-dialogs"></a>Comandos GOSUB, mediante la arquitectura de comandos en los cuadros de diálogo

La arquitectura de comandos de enrutamiento y permitir comandos funciona bien con ventanas de marco, elementos de menú, botones de barra de herramientas, los botones de barra de cuadro de diálogo, barras de controles y otros elementos de interfaz de usuario diseñadas para actualizar en la demanda y la ruta de comandos o identificadores de control a un principal destino del comando (normalmente la ventana de marco principal). Que tienen como destino comando principal puede enrutar las notificaciones de comando o un control a otros objetos de destino del comando según corresponda.

Un cuadro de diálogo (modal o no modal) puede beneficiarse de algunas de las características de la arquitectura de comandos si asigna el identificador de control del control de cuadro de diálogo con el identificador de comando adecuado. Compatibilidad con los cuadros de diálogo no es automática, por lo que es posible que deba escribir código adicional.

Tenga en cuenta que, para que todas estas características funcionen correctamente, los identificadores de comando deben ser > = 0 x 8000. Dado que muchos de los cuadros de diálogo podrían dirigirse a la misma trama, comandos compartidos deben ser > = 0 x 8000, mientras que el IDCs no compartidas en un cuadro de diálogo específico deben ser < = 0x7FFF.

Puede colocar un botón normal en un cuadro de diálogo modal normal con la IDC del botón establecido en el identificador de comando adecuado. Cuando el usuario selecciona el botón, el propietario del cuadro de diálogo (normalmente la ventana de marco principal) Obtiene el comando igual que cualquier otro comando. Esto se denomina un comando GOSUB puesto que normalmente se usa para que aparezca otro cuadro de diálogo (un GOSUB del primer cuadro de diálogo).

También puede llamar a la función `CWnd::UpdateDialogControls` en el cuadro de diálogo y pasarle la dirección de la ventana de marco principal. Esta función se habilita o deshabilita los controles de cuadro de diálogo en función de si cuentan con controladores de comandos en el marco. Esta función se invoca automáticamente para usted para barras de control de bucle de inactividad de la aplicación, pero se debe llamar directamente para los cuadros de diálogo normales que desee tener esta característica.

## <a name="when-onupdatecommandui-is-called"></a>Cuando se llama a ON_UPDATE_COMMAND_UI

Mantener el estado habilitado/comprueba de todos los de un programa elementos de menú todo el tiempo, puede ser un problema que consumen muchos recursos. Una técnica común es/comprobación de habilitación de los elementos de menú sólo cuando el usuario selecciona el elemento emergente. La implementación de MFC 2.0 de `CFrameWnd` controla el mensaje WM_INITMENUPOPUP y usa la arquitectura de enrutamiento de comandos para determinar los Estados de menús a través de los controladores ON_UPDATE_COMMAND_UI.

`CFrameWnd` También controla el mensaje WM_ENTERIDLE para describir el elemento seleccionado en el estado de la barra (también conocida como la línea del mensaje) de menú actual.

Estructura de menús de la aplicación, editada por Visual C++, se utiliza para representar los posibles comandos disponibles en el momento WM_INITMENUPOPUP. Los controladores ON_UPDATE_COMMAND_UI pueden modificar el estado o el texto de un menú o para usos avanzados (por ejemplo, la lista MRU del archivo o el menú emergente de los verbos OLE), realmente modificar la estructura de menú antes de que se dibuja el menú.

Se realiza el mismo tipo de procesamiento ON_UPDATE_COMMAND_UI para las barras de herramientas (y otras barras de control) cuando la aplicación entra en su bucle de inactividad. Consulte la *Class Library Reference* y [Nota técnica 31](../mfc/tn031-control-bars.md) para obtener más información sobre las barras de control.

## <a name="nested-pop-up-menus"></a>Menús emergentes anidados

Si usa una estructura de menús anidados, observará que se llama al controlador ON_UPDATE_COMMAND_UI del primer elemento de menú en el menú emergente en dos casos diferentes.

En primer lugar, se llama por el propio menú emergente. Esto es necesario porque los menús emergentes no tienen los identificadores y usamos el identificador del primer elemento de menú del menú emergente para hacer referencia a todo el menú emergente. En este caso, el *m_pSubMenu* variable miembro de la `CCmdUI` objeto será distinto de NULL y señale el menú emergente.

En segundo lugar, se llama justo antes de que son los elementos de menú en el menú emergente que se va a dibujar. En este caso, hace referencia el identificador para el primer elemento de menú y el *m_pSubMenu* variable miembro de la `CCmdUI` objeto será NULL.

Esto permite habilitar el menú emergente distinto de sus elementos de menú, pero es necesario escribir algún código con reconocimiento de menú. Por ejemplo, en un menú anidado con la estructura siguiente:

```Output
File>
    New>
    Sheet (ID_NEW_SHEET)
    Chart (ID_NEW_CHART)
```

Los comandos ID_NEW_SHEET y ID_NEW_CHART se pueden habilitar o deshabilitar de forma independiente. El **New** menú emergente debe habilitarse si se habilita cualquiera de los dos.

El controlador de comandos para ID_NEW_SHEET (el primer comando en el menú emergente) sería algo así:

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

El controlador de comandos para ID_NEW_CHART sería un controlador de comandos de actualización normal y un aspecto algo como:

```cpp
void CMyApp::OnUpdateNewChart(CCmdUI* pCmdUI)
{
    pCmdUI->Enable(m_bCanCreateChart);
}
```

## <a name="oncommand-and-onbnclicked"></a>ON_COMMAND y ON_BN_CLICKED

Las macros de mapa de mensajes para **ON_COMMAND** y **ON_BN_CLICKED** son los mismos. El comando y control notificación enrutamiento mecanismo de MFC utiliza solo el identificador de comando para decidir dónde enrutar a. Controlar las notificaciones con el código de notificación de control de cero (**BN_CLICKED**) se interpretan como comandos.

> [!NOTE]
> De hecho, todos los mensajes de notificación de control Ir a través de la cadena de comandos del controlador. Por ejemplo, es técnicamente posible para que pueda escribir un controlador de notificación de control para **EN_CHANGE** en la clase de documento. Esto no es aconsejable porque son pocas las aplicaciones prácticas de esta característica, no se admite la característica de ClassWizard y uso de la característica puede dar lugar a código frágil.

## <a name="disabling-the-automatic-disabling-of-button-controls"></a>Deshabilitar la desactivación automática de los controles de botón

Si se coloca un control de botón en una barra de cuadro de diálogo o en un cuadro de diálogo donde se está llamando a **CWnd::UpdateDialogControls** por su parte, observará que los botones que no tienen **ON_COMMAND** o **ON_UPDATE_COMMAND_UI** controladores se deshabilitará automáticamente para el marco de trabajo. En algunos casos, no necesitará tener un controlador, pero desea el botón que permanezca habilitado. La manera más fácil de lograr esto es agregar un controlador de comandos ficticio (fácil de hacer con el Asistente para clases) y no hacen nada en él.

## <a name="window-message-routing"></a>Enrutamiento de mensajes de ventana

El siguiente describe algunos temas más avanzados en las clases MFC y cómo el enrutamiento de mensajes de Windows y otros temas afectan a ellos. Solo se describe brevemente la información aquí. Hacer referencia a la *Class Library Reference* para obtener más información acerca de las API públicas. Consulte el código de fuente MFC library para obtener más información sobre los detalles de implementación.

Consulte [17 de nota técnica](../mfc/tn017-destroying-window-objects.md) para obtener más información sobre la limpieza de la ventana, un tema muy importante para todos los **CWnd**-las clases derivadas.

## <a name="cwnd-issues"></a>Problemas de CWnd

La función de miembro de la implementación **CWnd::OnChildNotify** proporciona una arquitectura extensible y eficaz para ventanas secundarias de (también denominados controles) enlazar o en caso contrario, se informará de los mensajes, comandos y control notificaciones que se envían a su elemento primario (o "propietario"). Si la ventana secundaria (/ control) es un C++ **CWnd** objeto, la función virtual **OnChildNotify** se llama primero con los parámetros del mensaje original (es decir, un **MSG**estructura). La ventana secundaria puede dejar el mensaje, comerlo o modificar el mensaje para el elemento primario (poco frecuente).

El valor predeterminado **CWnd** implementación controla los siguientes mensajes y utiliza el **OnChildNotify** gancho para permitir que los secundarios (controles) de windows para el primer acceso en el mensaje:

- **WM_MEASUREITEM** y **WM_DRAWITEM** (para automática dibujar)

- **WM_COMPAREITEM** y **WM_DELETEITEM** (para automática dibujar)

- **Mensajes WM_HSCROLL** y **WM_VSCROLL**

- **WM_CTLCOLOR**

- **WM_PARENTNOTIFY**

Observará el **OnChildNotify** enlace se usa para cambiar mensajes dibujados en dibujar automáticamente mensajes.

Además el **OnChildNotify** gancho, mensajes de desplazamiento tienen aún más el comportamiento de enrutamiento. Consulte a continuación para obtener más detalles sobre las barras de desplazamiento y orígenes de **mensajes WM_HSCROLL** y **WM_VSCROLL** mensajes.

## <a name="cframewnd-issues"></a>Problemas de CFrameWnd

El **CFrameWnd** clase proporciona la mayor parte de la interfaz de usuario y enrutamiento de comandos de actualización de implementación. Esto se utiliza principalmente para la ventana de marco principal de la aplicación (**CWinApp::m_pMainWnd**), pero se aplica a todas las ventanas de marco.

La ventana de marco principal es la ventana de la barra de menús y es el elemento primario de la barra de estado o la línea del mensaje. Consulte la explicación anterior sobre el enrutamiento de comandos y **WM_INITMENUPOPUP.**

El **CFrameWnd** clase proporciona administración de la vista activa. Los siguientes mensajes se enrutan a través de la vista activa:

- Todos los mensajes de comando (la vista activa Obtiene el primer acceso a ellos).

- **Mensajes WM_HSCROLL** y **WM_VSCROLL** (ver abajo) de barras de desplazamiento de mensajes procedentes del mismo nivel.

- **WM_ACTIVATE** (y **WM_MDIACTIVATE** para MDI) obtener convierten en llamadas a la función virtual **CView::OnActivateView**.

## <a name="cmdiframewndcmdichildwnd-issues"></a>CMDIFrameWnd/CMDIChildWnd problemas

Ambas clases de ventana de marco MDI derivan **CFrameWnd** y, por tanto, se activan para el mismo tipo de enrutamiento de comandos y actualización de la interfaz de usuario proporcionado en **CFrameWnd**. En una aplicación típica de MDI, sólo la ventana de marco principal (es decir, el **CMDIFrameWnd** objeto) que contiene la barra de menús y la barra de estado y, por tanto, es la fuente principal de la implementación del enrutamiento de comandos.

El esquema general de enrutamiento es que la ventana secundaria MDI activa Obtiene el primer acceso a los comandos. El valor predeterminado **PreTranslateMessage** funciones controlan las tablas de aceleradores para ambas ventanas secundarias de MDI (primero) y el marco MDI (segundo), así como los aceleradores de comando del sistema estándares de MDI normalmente se controlan mediante  **TranslateMDISysAccel** (última).

## <a name="scroll-bar-issues"></a>Problemas de la barra de desplazamiento

Al controlar el mensaje de desplazamiento (**mensajes WM_HSCROLL**/**OnHScroll** o **WM_VSCROLL**/**OnVScroll**), debe intentar escribir el código del controlador, por lo que no depende de dónde procede el mensaje de la barra de desplazamiento. Esto no es solo un problema de Windows general, dado que los mensajes de desplazamiento pueden proceder de desplazamiento es true, los controles de barra o desde **WS_HSCROLL**/**WS_VSCROLL** barras que no son controles de barra de desplazamiento de desplazamiento.

Extiende MFC que para permitir que los controles de barra de desplazamiento ser secundarios o elementos del mismo nivel de la ventana que se va a desplazar (de hecho, la relación primario-secundario entre la barra de desplazamiento y la ventana que se va a desplazar puede ser cualquier cosa). Esto es especialmente importante para las barras de desplazamiento compartido con ventanas divisoras. Consulte [29 de nota técnica](../mfc/tn029-splitter-windows.md) para obtener más información sobre la implementación de **CSplitterWnd** incluyendo más información en comparten problemas de la barra de desplazamiento.

En una nota al margen, hay dos **CWnd** donde los estilos de barra de desplazamiento especificados en creación el tiempo que las clases derivadas se capturan y no se pasan a Windows. Cuando se pasa a una rutina de creación, **WS_HSCROLL** y **WS_VSCROLL** puede establecerse de forma independiente, pero después de la creación no se puede cambiar. Por supuesto, no directamente debe probar o establecer los bits de estilo WS_SCROLL de la ventana que hayan creado.

Para **CMDIFrameWnd** los estilos de barra de desplazamiento se pasa a **crear** o **LoadFrame** se utilizan para crear el MDICLIENT. Si desea tener un área desplazable de MDICLIENT (como el Windows Administrador de programas) asegúrese de establecer tanto la barra de desplazamiento estilos (**WS_HSCROLL** &#124; **WS_VSCROLL**) para el estilo utilizado para crear el **CMDIFrameWnd**.

Para **CSplitterWnd** los estilos de barra de desplazamiento se aplican a las barras de desplazamiento compartido especial para las regiones del divisor. Para las ventanas divisoras estáticas, normalmente no establecerá cualquier estilo de barra de desplazamiento. Para las ventanas divisoras dinámicas, normalmente, tendrá el conjunto de estilos para la dirección se dividirán, es decir, de la barra de desplazamiento **WS_HSCROLL** que puede dividir las filas, **WS_VSCROLL** que puede dividir las columnas.

## <a name="see-also"></a>Vea también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)
