---
title: 'TN021: Comandos y enrutamiento de mensajes | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.routing
dev_langs: C++
helpviewer_keywords:
- TN021
- command routing [MFC], technical note TN021
- Windows messages [MFC], routing
ms.assetid: b5952c8b-123e-406c-a36d-a6ac7c6df307
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1854be249db91257228e6dab70fc7ff2f50664ce
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="tn021-command-and-message-routing"></a>TN021: Enrutamiento de comandos y mensajes
> [!NOTE]
>  La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea. Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos. Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.  
  
 Esta nota describe la arquitectura de enrutamiento y el envío de comandos, así como temas avanzados de enrutamiento de mensajes de ventana general.  
  
 Consulte Visual C++ para obtener información general sobre las arquitecturas aquí descritas, en especial la distinción entre mensajes, las notificaciones del control y los comandos de Windows. Esta nota se supone que está muy familiarizado con los problemas descritos en la documentación impresa y solo trata temas muy avanzados.  
  
## <a name="command-routing-and-dispatch-mfc-10-functionality-evolves-to-mfc-20-architecture"></a>Funcionalidad de envío y enrutamiento de comandos MFC 1.0 evoluciona a MFC 2.0 arquitectura  
 Windows tiene el **WM_COMMAND** mensaje que se sobrecarga para proporcionar notificaciones de los comandos de menú, teclas de aceleración y notificaciones del control de cuadro de diálogo.  
  
 MFC 1.0 depende de que un poco al permitir que un controlador de comandos (por ejemplo, "OnFileNew") un **CWnd** derivadas de la clase a se llama en respuesta a una determinada **WM_COMMAND**. Esto está pegado junto con una estructura de datos denominada el mapa de mensajes y da como resultado un mecanismo muy eficaz del espacio del comando.  
  
 MFC 1.0 también proporcionan una funcionalidad adicional para separar las notificaciones del control de mensajes de comando. Comandos se representan mediante un identificador de 16 bits, conocido también como un identificador de comando. Comandos normalmente se inician desde una **CFrameWnd** (es decir, una selección de menú o un acelerador traducido) y se enrutan a una variedad de otras ventanas.  
  
 MFC 1.0 utiliza el enrutamiento de comandos en un sentido limitado para la implementación de interfaz de múltiples documentos (MDI). (Una ventana de marco MDI delegar comandos en la ventana de formulario secundario MDI activada).  
  
 Esta funcionalidad se ha generalizado y amplía en MFC 2.0 para permitir los comandos controlando una gama más amplia de objetos (no solo los objetos de ventana). Proporciona más formal y arquitectura extensible para el enrutamiento de mensajes y vuelve a utilizar el enrutamiento de destino de comandos para controlar no sólo de comandos, sino también para actualizar los objetos de interfaz de usuario (por ejemplo, elementos de menú y botones de barra de herramientas) para que refleje la disponibilidad actual de un comando .  
  
## <a name="command-ids"></a>Identificadores de comando  
 Vea Visual C++ para obtener una explicación del comando enrutamiento y proceso de enlace. [Nota técnica 20](../mfc/tn020-id-naming-and-numbering-conventions.md) contiene información sobre los nombres de identificador.  
  
 Se utiliza el prefijo genérico "ID_" para los identificadores de comando. Los identificadores de comando son > = 0 x 8000. La barra de estado o la línea de mensaje mostrará la cadena de descripción de comandos si hay un recurso STRINGTABLE con los mismos identificadores como identificador del comando.  
  
 En los recursos de la aplicación, un comando que puede identificador aparece en varios lugares:  
  
-   En un recurso STRINGTABLE tiene el mismo identificador que el símbolo del sistema de línea de mensaje.  
  
-   En posiblemente muchos recursos de menú que se adjuntan a elementos de menú que invocan el mismo comando.  
  
-   (Avanzado) en un botón de cuadro de diálogo para un comando GOSUB.  
  
 En el código fuente de la aplicación, un comando que puede identificador aparece en varios lugares:  
  
-   En el recurso. H (u otro archivo de encabezado de símbolos principal) para definir los identificadores de comandos específicos de la aplicación.  
  
-   Por ejemplo, en una matriz de Id. que se utiliza para crear una barra de herramientas.  
  
-   En un **ON_COMMAND** macro.  
  
-   Por ejemplo, en un **ON_UPDATE_COMMAND_UI** macro.  
  
 Actualmente, la única implementación de MFC que requiere identificadores de comando ser > = 0 x 8000 es la implementación de los cuadros de diálogo y comandos de GOSUB.  
  
## <a name="gosub-commands-using-command-architecture-in-dialogs"></a>Comandos GOSUB, mediante la arquitectura de comandos en los cuadros de diálogo  
 La arquitectura de comandos de enrutamiento y permitir comandos funciona bien con ventanas de marco, elementos de menú, botones de barra de herramientas, botones de la barra de cuadro de diálogo, barras de controles y otros elementos de interfaz de usuario diseñadas para actualizar en la demanda y la ruta de comandos o identificadores de controles a un principal destino del comando (normalmente en la ventana de marco principal). Que tienen como destino comando principal puede enrutar las notificaciones de comando o un control a otros objetos de destino del comando según corresponda.  
  
 Un cuadro de diálogo (modal o no modal) puede beneficiarse de algunas de las características de la arquitectura de comandos si asigna el identificador del control del control de cuadro de diálogo para el identificador de comando adecuado. Compatibilidad con los cuadros de diálogo no es automática, por lo que puede que tenga que escribir código adicional.  
  
 Tenga en cuenta que, para que todas estas características para que funcione correctamente, los identificadores de comando deben ser > = 0 x 8000. Puesto que muchos de los cuadros de diálogo obtener pudieron enrutar al mismo fotograma, comandos compartidos deben ser > = 0 x 8000, mientras que la IDCs no compartidas en un cuadro de diálogo específico deben ser < = 0x7FFF.  
  
 Puede colocar un botón normal en un cuadro de diálogo modal normal con la IDC del botón establecido en el identificador de comando adecuado. Cuando el usuario selecciona el botón, el propietario del cuadro de diálogo (normalmente en la ventana de marco principal) recibe el comando igual que cualquier otro comando. Esto se denomina un comando GoSub '. Puesto que normalmente se usa para abrir otro cuadro de diálogo (GOSUB del primer cuadro de diálogo).  
  
 También puede llamar a la función **CWnd::UpdateDialogControls** en el cuadro de diálogo y pasarle la dirección de la ventana de marco principal. Esta función se habilita o deshabilita los controles de cuadro de diálogo en función de si cuentan con controladores de comandos en el marco. Esta función se invoca automáticamente para usted para las barras de control en el bucle inactivo de la aplicación, pero se debe llamar directamente para los cuadros de diálogo normales que se va a tener esta característica.  
  
## <a name="when-onupdatecommandui-is-called"></a>Cuando se llama a ON_UPDATE_COMMAND_UI  
 Mantener el estado habilitado/comprueba de todos los de un programa elementos de menú en todo momento puede ser un problema consumen muchos recursos. Una técnica común consiste en Habilitar/proteger elementos de menú sólo cuando el usuario selecciona el elemento emergente. La implementación de MFC 2.0 de **CFrameWnd** controla la **WM_INITMENUPOPUP** el mensaje y utiliza la arquitectura de enrutamiento de comandos para determinar los Estados de menús a través de **ON_UPDATE_COMMAND_ Interfaz de usuario** controladores.  
  
 **CFrameWnd** también controla la **WM_ENTERIDLE** mensaje para describir el menú actual elemento seleccionado en el estado de la barra (también conocido como la línea del mensaje).  
  
 Estructura de menús de la aplicación y editado por Visual C++, se utiliza para representar los posibles comandos disponibles en **WM_INITMENUPOPUP** tiempo. **ON_UPDATE_COMMAND_UI** controladores pueden modificar el estado o el texto de un menú, o para usos avanzados (por ejemplo, la lista de archivos utilizados más Recientemente o el menú emergente de verbos OLE), modifica realmente la estructura de menú antes de se dibuja el menú.  
  
 El mismo tipo de **ON_UPDATE_COMMAND_UI** se realiza un procesamiento para las barras de herramientas (y otras barras de control) cuando la aplicación entra en el bucle inactivo. Consulte la *Class Library Reference* y [Nota técnica 31](../mfc/tn031-control-bars.md) para obtener más información sobre las barras de control.  
  
## <a name="nested-pop-up-menus"></a>Menús emergentes anidados  
 Si se utiliza una estructura de menú anidado, observará que el **ON_UPDATE_COMMAND_UI** se llamará al controlador para el primer elemento de menú en el menú emergente en dos casos diferentes.  
  
 En primer lugar, se llama por el menú emergente. Esto es necesario porque los menús emergentes no tienen identificadores y se utiliza el identificador del primer elemento de menú del menú emergente para hacer referencia a todo el menú emergente. En este caso, el **m_pSubMenu** variable miembro de la **CCmdUI** objeto será distinto de NULL y apuntará al menú emergente.  
  
 En segundo lugar, se llama justo antes de que los elementos de menú en el menú emergente que se van a dibujar. En este caso, hace referencia el identificador para el primer elemento de menú y la **m_pSubMenu** variable miembro de la **CCmdUI** objeto será NULL.  
  
 Esto permite habilitar el menú emergente distinto de sus elementos de menú, pero necesita que escriba algún código con reconocimiento de menú. Por ejemplo, en un menú anidado con la estructura siguiente:  
  
```  
File>  
    New> 
    Sheet (ID_NEW_SHEET)  
    Chart (ID_NEW_CHART)  
```  
  
 Los comandos ID_NEW_SHEET y ID_NEW_CHART pueden habilitar o deshabilitar por separado. El **New** menú emergente debe habilitarse si cualquiera de los dos está habilitada.  
  
 El controlador de comandos para ID_NEW_SHEET (el primer comando en el menú emergente) sería algo parecido:  
  
```  
void CMyApp::OnUpdateNewSheet(CCmdUI* pCmdUI)  
{  
    if (pCmdUI->m_pSubMenu != NULL)  
 { *// enable entire pop-up for "New" sheet and chart  
    BOOL bEnable = m_bCanCreateSheet || m_bCanCreateChart;  
 *// CCmdUI::Enable is a no-op for this case,
    so we *//   must do what it would have done.  
    pCmdUI->m_pMenu->EnableMenuItem(pCmdUI->m_nIndex, 
    MF_BYPOSITION |   
 (bEnable  MF_ENABLED : (MF_DISABLED | MF_GRAYED)));

    return; 
 } *// otherwise just the New Sheet command  
    pCmdUI->Enable(m_bCanCreateSheet);

} 
```  
  
 El controlador de comandos para ID_NEW_CHART sería un controlador de comandos de actualización normal y busque un resultado similar:  
  
```  
void CMyApp::OnUpdateNewChart(CCmdUI* pCmdUI)  
{  
    pCmdUI->Enable(m_bCanCreateChart);

} 
```  
  
## <a name="oncommand-and-onbnclicked"></a>ON_COMMAND y ON_BN_CLICKED  
 Las macros de mapa de mensajes para **ON_COMMAND** y **ON_BN_CLICKED** son los mismos. El comando y control de notificación enrutamiento mecanismo MFC sólo usa el identificador de comando para decidir dónde enrutarlo a. Controlar notificaciones con el código de notificación de control de cero (**BN_CLICKED**) se interpretan como comandos.  
  
> [!NOTE]
>  De hecho, todos los mensajes de notificación de control irán a través de la cadena de controlador de comandos. Por ejemplo, es técnicamente posible de escribir un controlador de notificación de control para **EN_CHANGE** en la clase de documento. Esto no es aconsejable generalmente porque son pocas las aplicaciones prácticas de esta característica, la característica no es compatible con ClassWizard y uso de la característica puede dar lugar a código frágil.  
  
## <a name="disabling-the-automatic-disabling-of-button-controls"></a>Deshabilitar la desactivación automática de controles de botón  
 Si se coloca un control de botón en una barra de cuadro de diálogo o en un cuadro de diálogo con dónde se está llamando a **CWnd::UpdateDialogControls** por su cuenta, observará que los botones que no tienen **ON_COMMAND** o **ON_UPDATE_COMMAND_UI** controladores se deshabilitará automáticamente para el marco de trabajo. En algunos casos, no debe tener un controlador, pero le interesará el botón que permanezca habilitado. La manera más fácil de lograr esto consiste en Agregar un controlador de comandos ficticio (fácil con ClassWizard) y no hacen nada en él.  
  
## <a name="window-message-routing"></a>Enrutamiento de mensajes de ventana  
 A continuación describen algunos de los temas más avanzados en las clases MFC y cómo el enrutamiento de mensajes de Windows y otros temas relacionados afectan a ellos. La información aquí solo se describe brevemente. Hacer referencia a la *Class Library Reference* para obtener más información acerca de las API públicas. Consulte el código de la biblioteca MFC para obtener más información sobre los detalles de implementación.  
  
 Consulte [17 de nota técnica](../mfc/tn017-destroying-window-objects.md) para obtener más información sobre la limpieza de la ventana, un tema muy importante para todos los **CWnd**-las clases derivadas.  
  
## <a name="cwnd-issues"></a>Problemas de CWnd  
 La función de miembro de la implementación **CWnd::OnChildNotify** proporciona una arquitectura extensible y eficaz de las ventanas de secundarias (también conocido como controles) enlazar o de lo contrario estar informado de mensajes, los comandos y control notificaciones que vaya a su elemento primario (o "propietario"). Si la ventana secundaria (/ control) es C++ **CWnd** objeto, la función virtual **OnChildNotify** se llama primero con los parámetros del mensaje original (es decir, un **MSG**estructura). La ventana secundaria puede dejar el mensaje por sí solo, comer o modificar el mensaje para el elemento primario (poco frecuente).  
  
 El valor predeterminado **CWnd** implementación controla los siguientes mensajes y utiliza el **OnChildNotify** enlace para permitir secundarios windows (controles) para el primer acceso a un mensaje:  
  
- **WM_MEASUREITEM** y **WM_DRAWITEM** (para sí mismo dibuje)  
  
- **WM_COMPAREITEM** y **WM_DELETEITEM** (para sí mismo dibuje)  
  
- **Mensajes WM_HSCROLL** y **WM_VSCROLL**  
  
- **WM_CTLCOLOR**  
  
- **WM_PARENTNOTIFY**  
  
 Observará el **OnChildNotify** enlace se usa para variables mensajes dibujado por el propietario en sí mismo dibujar mensajes.  
  
 Además el **OnChildNotify** enlace, mensajes de desplazamiento tienen aún más el comportamiento de enrutamiento. Vea a continuación para obtener más detalles sobre las barras de desplazamiento y orígenes de **mensajes WM_HSCROLL** y **WM_VSCROLL** mensajes.  
  
## <a name="cframewnd-issues"></a>Problemas de CFrameWnd  
 El **CFrameWnd** clase proporciona la mayor parte de la interfaz de usuario y de enrutamiento de comandos actualizando la implementación. Esto se utiliza principalmente para la ventana de marco principal de la aplicación (**CWinApp::m_pMainWnd**), pero se aplica a todas las ventanas de marco.  
  
 La ventana de marco principal es la ventana con la barra de menús y es el elemento primario de la barra de estado o la línea del mensaje. Consulte la discusión anterior en enrutamiento de comandos y **WM_INITMENUPOPUP.**  
  
 El **CFrameWnd** clase proporciona administración de la vista activa. Los siguientes mensajes se enrutan a través de la vista activa:  
  
-   Todos los mensajes de comando (primer acceso a ellos pasa a la vista activa).  
  
- **Mensajes WM_HSCROLL** y **WM_VSCROLL** (ver abajo) de barras de desplazamiento de mensajes del mismo nivel.  
  
- **WM_ACTIVATE** (y **WM_MDIACTIVATE** para MDI) obtener se convierten en llamadas a la función virtual **CView::OnActivateView**.  
  
## <a name="cmdiframewndcmdichildwnd-issues"></a>CMDIFrameWnd/CMDIChildWnd problemas  
 Ambas clases de ventana de marco MDI derivan de **CFrameWnd** y, por tanto, se habilitan para el mismo tipo de enrutamiento de comandos y actualización de la interfaz de usuario proporcionado en **CFrameWnd**. En una aplicación MDI típica, la ventana de marco principal (es decir, el **CMDIFrameWnd** objeto) que contiene la barra de menús y la barra de estado y, por tanto, es el origen principal de la implementación de enrutamiento de comandos.  
  
 El esquema de enrutamiento general es que la ventana secundaria MDI activa obtiene acceso primero a los comandos. El valor predeterminado **PreTranslateMessage** funciones controlen las tablas de aceleradores para ambas ventanas secundarias MDI (primero) y el marco MDI (segundo), así como los aceleradores de comando del sistema MDI estándares normalmente se controlan mediante  **TranslateMDISysAccel** (última).  
  
## <a name="scroll-bar-issues"></a>Problemas de la barra de desplazamiento  
 Al administrar los mensajes de desplazamiento (**mensajes WM_HSCROLL**/**OnHScroll** o **WM_VSCROLL**/**OnVScroll**), debe intentar escribir el código del controlador, por lo que no depende de dónde procede el mensaje de la barra de desplazamiento. Esto no es solo un problema de Windows general, ya que los mensajes de desplazamiento pueden proceder de true barra de desplazamiento controles o de **WS_HSCROLL**/**WS_VSCROLL** barras que no son controles de barra de desplazamiento de desplazamiento.  
  
 MFC extiende ello para permitir que para que los controles de barra de desplazamiento ser secundarios o elementos del mismo nivel de la ventana que se desplaza (de hecho, la relación de elementos primarios y secundarios entre la barra de desplazamiento y la ventana que se va a desplazar puede ser cualquier cosa). Esto es especialmente importante para las barras de desplazamiento compartido con las ventanas divisoras. Consulte [29 de nota técnica](../mfc/tn029-splitter-windows.md) para obtener más información sobre la implementación de **CSplitterWnd** con más información sobre compartido problemas de la barra de desplazamiento.  
  
 En una nota al margen, hay dos **CWnd** donde los estilos de barra de desplazamiento especificados en crear tiempo que las clases derivadas se haya quedado bloqueadas y no se pasan a Windows. Cuando se pasa a una rutina de creación, **WS_HSCROLL** y **WS_VSCROLL** puede establecerse de forma independiente, pero después de que no se puede cambiar la creación. Por supuesto, debe probar no directamente o establecer los bits de estilo WS_SCROLL de la ventana que han creado.  
  
 Para **CMDIFrameWnd** los estilos de barra de desplazamiento se pasa a **crear** o **LoadFrame** se utilizan para crear el MDICLIENT. Si desea tener un área desplazable de MDICLIENT (al igual que el programa Administrador de Windows) no olvide establecer tanto la barra de desplazamiento estilos (**WS_HSCROLL** &#124; **WS_VSCROLL**) para el estilo utilizado para crear el **CMDIFrameWnd**.  
  
 Para **CSplitterWnd** los estilos de barra de desplazamiento que se aplican a las barras de desplazamiento compartido especial para las regiones del divisor. Para las ventanas divisoras estáticas, normalmente no establecerá cualquier estilo de barra de desplazamiento. Para las ventanas divisoras dinámicas, normalmente tendrá la barra estilo establecido para el que se dividirá, es decir, las direcciones de desplazamiento **WS_HSCROLL** que puede dividir filas, **WS_VSCROLL** que puede dividir las columnas.  
  
## <a name="see-also"></a>Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)

