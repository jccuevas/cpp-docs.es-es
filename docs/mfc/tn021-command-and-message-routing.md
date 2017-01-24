---
title: "TN021: Enrutamiento de comandos y mensajes | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.routing"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "enrutamiento de comandos [C++], Nota técnica de TN021"
  - "TN021"
  - "mensajes de Windows [C++], enrutar"
ms.assetid: b5952c8b-123e-406c-a36d-a6ac7c6df307
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN021: Enrutamiento de comandos y mensajes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea.  Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos.  Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.  
  
 Esta nota describe la arquitectura de enrutamiento y el envío de un comando así como temas avanzados en el enrutamiento de mensajes general de la ventana.  
  
 Consulte en Visual C\+\+ para los detalles generales en arquitecturas descritas a continuación, especialmente la diferencia entre los mensajes de Windows, las notificaciones del control, y los comandos.  Esta nota se supone que está muy familiarizado con los problemas descritos en la documentación impresa y solo los temas muy avanzadas de direcciones.  
  
## Funcionalidad Evolves MFC 1,0 de enrutamiento y el envío de un comando a la arquitectura de MFC 2,0  
 Windows tiene el mensaje de **WM\_COMMAND** que se sobrecarga para proporcionar notificaciones de los comandos de menú, de teclas de aceleración y de notificaciones de la diálogo\- CONTROL.  
  
 MFC 1,0 compilaciones que algún permitiendo que un controlador de comandos \(por ejemplo, “OnFileNew”\) en una clase derivada de **CWnd** obtenga denominado en respuesta a **WM\_COMMAND**concreto.  Esto se pega junto con una estructura de datos con el mapa de mensajes, y los resultados en un mecanismo muy espacio\- eficaz de comando.  
  
 Función adicional también proporcionada de MFC 1,0 para separar las notificaciones del control de mensajes del comando.  Un identificador de 16 bits representan los comandos, conocido a veces como identificador de comando  Los comandos salen de **CFrameWnd** \(es decir, un menú seleccione o un acelerador traducido\) y obtienen normalmente enrutar a una variedad de otras ventanas.  
  
 MFC 1,0 usa el enrutamiento de comandos en un sentido limitado para la implementación de la interfaz de múltiples documentos \(MDI\). \(Comandos de MDI del cuadro de un delegado desde la ventana hasta la ventana secundaria MDI activo.\)  
  
 Esta funcionalidad se ha general y se ha mejorado en MFC 2,0 para permitir que los comandos administran un intervalo mayor de objetos \(no sólo objetos de la ventana\).  Proporciona una arquitectura más formal y más extensible para distribuir mensajes y reutiliza el enrutamiento del destino de comando para no solo control de comandos, sino también para actualizar objetos de interfaz de usuario \(como elementos de menú y botones de la barra de herramientas\) para reflejar la disponibilidad actual de un comando.  
  
## Id. de comando  
 Vea Visual C\+\+ para obtener una explicación del enrutamiento de comandos y el proceso de enlace.  [Nota técnica 20](../mfc/tn020-id-naming-and-numbering-conventions.md) contiene información en la nomenclatura de identificador.  
  
 Utilizamos el prefijo genérico “ID\_” para los id. del comando.  Los id. de comando son \>\= 0x8000.  La línea de mensajes o la barra de estado mostrará la cadena de descripción del comando si hay un recurso de STRINGTABLE con los mismos id. que el identificador de comando  
  
 En los recursos de la aplicación, se puede id del comando aparecerá en varios lugares:  
  
-   En un recurso de STRINGTABLE que tiene el mismo identificador que el indicador de línea de mensajes.  
  
-   En posiblemente muchos recursos de MENU asociados a los elementos de menú que invocan el mismo comando.  
  
-   \(AVANZADO\) en un botón del cuadro de diálogo para un comando de GOSUB.  
  
 En el código fuente de la aplicación, se puede id del comando aparecerá en varios lugares:  
  
-   En el RESOURCE.H \(u otro archivo principal de encabezado de símbolos\) para definir id. específicos de la aplicación del comando.  
  
-   PERHAPS en una matriz del identificador utilizado para crear una barra de herramientas.  
  
-   En una macro de **ON\_COMMAND** .  
  
-   PERHAPS en una macro de **ON\_UPDATE\_COMMAND\_UI** .  
  
 Actualmente, la única implementación en MFC que requiere id. de comando es \>\= 0x8000 es la implementación de los cuadros y de los comandos de GOSUB.  
  
## Comandos de GOSUB, arquitectura de comando de Utilizar en cuadros de diálogo  
 La arquitectura del enrutamiento y los comandos el habilitar funciona bien con las ventanas de marco, elementos de menú, los botones de la barra de herramientas, los botones de la barra de cuadro de diálogo, otras barras de controles y otros elementos de interfaz de usuario diseñados para actualizar a petición y distribuir comandos o id. del control a un destino principal de comando \(normalmente la ventana de marco principal\).  Que el destino principal de comando puede distribuir las notificaciones de comandos o de control a otros objetos del destino de comando según corresponda.  
  
 Un diálogo \(modal o no modal\) puede beneficiarse de algunas de las características de la arquitectura de comando si asigna el identificador de control de cuadro de diálogo al identificador de comando apropiada  Compatibilidad para los cuadros de diálogo no es automática, por lo que puede tener que escribir código adicional.  
  
 Observe que para que todas estas características funcionen correctamente, el comando que los id. deben ser \>\= 0x8000.  Dado que muchos cuadros de diálogo pueden obtener a enrutar al mismo cuadro, los comandos compartidos deben ser \>\= 0x8000, mientras que el IDCs nonshared en un diálogo específico debe ser \<\= 0x7FFF.  
  
 Puede colocar un botón normal en un diálogo modal normal con IDC de botón establecido en el identificador de comando apropiada  Cuando el usuario selecciona el botón, el propietario del diálogo \(normalmente la ventana de marco principal\) obtiene el comando como cualquier otro comando.  Esto se denomina un comando de GOSUB puesto que se utiliza normalmente para abrir otro diálogo \(un GOSUB del primer diálogo\).  
  
 También puede llamar a la función **CWnd::UpdateDialogControls** en el diálogo y pasarle la dirección de la ventana de marco principal.  Esta función habilitará o deshabilitará los controles de cuadro de diálogo basándose en si tienen controladores de comandos en el cuadro.  Esta función se denomina automáticamente automáticamente para las barras de controles en el bucle de inactividad de la aplicación, pero debe llamar directamente para los cuadros de diálogo normales que desea tener esta característica.  
  
## Cuando se llama a ON\_UPDATE\_COMMAND\_UI  
 Mantener el estado habilitado\/activada de todos los elementos de menú de un programa todo el tiempo pueden ser un problema de computación.  Una técnica común es habilitar\/elementos de menú comprobados sólo cuando el usuario selecciona el MENU EMERGENTE.  Implementación de MFC 2,0 de **CFrameWnd** controla el mensaje de **WM\_INITMENUPOPUP** y utiliza la arquitectura de enrutamiento de comandos para determinar los estados de menús a través de los controladores de **ON\_UPDATE\_COMMAND\_UI** .  
  
 **CFrameWnd** también controla el mensaje de **WM\_ENTERIDLE** para describir el elemento de menú actual seleccionado en la barra de estado \(también conocida como línea de mensajes\).  
  
 La estructura de menú de una aplicación, editar en Visual C\+\+, se utiliza para representar los posibles comandos disponibles en tiempo de **WM\_INITMENUPOPUP** .  Los controladores de**ON\_UPDATE\_COMMAND\_UI** pueden modificar el estado o el texto de un menú, o para avanzadas utilizan \(como la lista de archivos usados recientemente del archivo o el menú emergente OLE de verbos\), modificar realmente la estructura de menú antes de que se dibuje el menú.  
  
 La misma ordenación de procesamiento de **ON\_UPDATE\_COMMAND\_UI** se hace para las barras de herramientas \(y otras barras de controles\) cuando la aplicación incorpora el bucle inactivo.  Vea *la biblioteca de clases de referencia* y  [Nota técnica 31](../mfc/tn031-control-bars.md) para obtener más información sobre las barras de controles.  
  
## Menús emergentes anidados  
 Si utiliza una estructura de menú anidadas, observará que se llama al controlador de **ON\_UPDATE\_COMMAND\_UI** para el primer elemento de menú del menú emergente de dos diferentes casos.  
  
 Primero, se llama a para el elemento emergente propio.  Esto es necesario porque los menús emergentes no tienen id. y se utiliza el identificador del primer elemento de menú del elemento emergente para hacer referencia al elemento emergente completo.  En este caso, la variable miembro de **m\_pSubMenu** del objeto de **CCmdUI** se no null e indicará al menú emergente.  
  
 En segundo lugar, se llama inmediatamente antes que los elementos de menú del menú emergente deben ser dibujados.  En este caso, el identificador consulta únicamente el primer elemento de menú y la variable miembro de **m\_pSubMenu** del objeto de **CCmdUI** serán NULL.  
  
 Esto permite habilitar el menú emergente distinto de sus elementos de menú, pero es necesario escribir a algún menú código monitores.  Por ejemplo, en un menú anidado con la siguiente estructura:  
  
```  
File>  
    New>  
        Sheet (ID_NEW_SHEET)  
        Chart (ID_NEW_CHART)  
```  
  
 Los comandos de ID\_NEW\_SHEET y de ID\_NEW\_CHART pueden habilitar o deshabilitar independientemente.  El menú emergente de **new** debe estar habilitado si cualquiera de los dos está habilitada.  
  
 El controlador de comandos para ID\_NEW\_SHEET \(el primer comando del elemento emergente\) será similar a:  
  
```  
void CMyApp::OnUpdateNewSheet(CCmdUI* pCmdUI)  
{  
    if (pCmdUI->m_pSubMenu != NULL)  
    {  
        // enable entire pop-up for "New" sheet and chart  
        BOOL bEnable = m_bCanCreateSheet || m_bCanCreateChart;  
  
        // CCmdUI::Enable is a no-op for this case, so we  
        //   must do what it would have done.  
        pCmdUI->m_pMenu->EnableMenuItem(pCmdUI->m_nIndex,  
            MF_BYPOSITION |   
                (bEnable ? MF_ENABLED : (MF_DISABLED | MF_GRAYED)));  
        return;  
    }  
    // otherwise just the New Sheet command  
    pCmdUI->Enable(m_bCanCreateSheet);  
}  
```  
  
 El controlador de comandos para ID\_NEW\_CHART sería controlador normal del comando de actualización y será similar a:  
  
```  
void CMyApp::OnUpdateNewChart(CCmdUI* pCmdUI)  
{  
    pCmdUI->Enable(m_bCanCreateChart);  
}  
```  
  
## ON\_COMMAND y ON\_BN\_CLICKED  
 Las macros de mapa de mensajes para **ON\_COMMAND** y **ON\_BN\_CLICKED** son iguales.  El mecanismo de enrutamiento de notificación de comando y de control MFC utiliza solo el identificador de comando para decidir dónde distribuir a.  Las notificaciones del Control con el código de notificación de control de cero \(**BN\_CLICKED**\) se interpretan como comandos.  
  
> [!NOTE]
>  De hecho, todos los mensajes de notificación de control atraviesan la cadena de controlador de comandos.  Por ejemplo, es técnicamente posible escribir un controlador de notificación de control para **EN\_CHANGE** en la clase del documento.  Esto no suele ser aconsejable porque las aplicaciones prácticas de esta característica son pocas, la característica no es compatible con ClassWizard, y el uso de características puede ocasionar código frágil.  
  
## Deshabilitar deshabilitar automático de controles de botón  
 Si se coloca un control de botón de una barra de cuadro de diálogo, o en un diálogo mediante donde está llamando **CWnd::UpdateDialogControls** en dispone, observará que los botones que no tienen controladores de **ON\_COMMAND** o de **ON\_UPDATE\_COMMAND\_UI** automáticamente estarán deshabilitadas automáticamente por el marco.  En algunos casos, no necesitará tener un controlador, sino que deseará el botón sigan siendo habilitado.  La manera más fácil de lograrlo es agregar un controlador ficticio de comando \(fácil hacer con ClassWizard\) y no hacer nada de ella.  
  
## Enrutamiento de mensajes de la ventana  
 A continuación se describe más temas avanzados en las clases MFC y cómo el enrutamiento de mensajes de Windows y otros temas las afectan a.  Información aquí se describe sólo brevemente.  Consulte *la referencia de la biblioteca de clases* para obtener más información sobre las API públicas.  Consulte el código fuente de la biblioteca MFC para obtener más información sobre los detalles de implementación.  
  
 Hace referencia a [Nota técnica 17](../mfc/tn017-destroying-window-objects.md) para los detalles de limpieza de la ventana, un tema muy importante para todo el **CWnd**\- clases derivadas.  
  
## Problemas de CWnd  
 La función **CWnd::OnChildNotify** miembro de implementación proporciona una arquitectura eficaz y extensible para ventanas secundarias \(también conocidas como controles\) el enlace o sea de otra manera informada de mensajes, de comandos, y las notificaciones del control que van a su elemento primario \(o a “propietario”\).  Si la ventana secundaria \(\/control\) es el propio objeto de c\+\+. **CWnd** , la función virtual **OnChildNotify** se denomina primero con los parámetros del mensaje original \(es decir, una estructura de **MSG** \).  La ventana secundaria puede salir de mensaje único, comerlo, o modificar el mensaje para el elemento primario \(poco\).  
  
 La implementación de **CWnd** predeterminado controla los mensajes siguientes y utiliza el enlace de **OnChildNotify** para permitir las ventanas secundarias \(controles\) al primer acceso en el mensaje:  
  
-   **WM\_MEASUREITEM** y **WM\_DRAWITEM** \(para el uno mismo\-dibujo\)  
  
-   **WM\_COMPAREITEM** y **WM\_DELETEITEM** \(para el uno mismo\-dibujo\)  
  
-   **WM\_HSCROLL** y **WM\_VSCROLL**  
  
-   **WM\_CTLCOLOR**  
  
-   **WM\_PARENTNOTIFY**  
  
 Observará el enlace de **OnChildNotify** se utiliza para cambiar mensajes de propietario\- dibuje mensajes de uno mismo\- dibujo.  
  
 Además de enlace de **OnChildNotify** , los mensajes de desplazamiento tienen comportamiento adicional de enrutamiento.  Vea más adelante para obtener más información sobre las barras de desplazamiento y los orígenes de los mensajes de **WM\_HSCROLL** y de **WM\_VSCROLL** .  
  
## Problemas de CFrameWnd  
 La clase de **CFrameWnd** proporciona la mayor parte del enrutamiento y la interfaz de usuario de comando que actualiza la implementación.  Esto se utiliza principalmente para la ventana de marco principal de la aplicación \(**CWinApp::m\_pMainWnd**\) pero se aplica a todas las ventanas de marco.  
  
 La ventana de marco principal es la ventana con la barra de menús y es el elemento primario de la barra de estado o de la línea de mensajes.  Consulte la descripción anterior en el enrutamiento y **WM\_INITMENUPOPUP.**de comando  
  
 La clase de **CFrameWnd** proporciona la administración de la vista activa.  Los siguientes mensajes se distribuyen con la vista activa:  
  
-   Todos los mensajes de comando \(la vista activa obtiene el primer acceso a ellos\).  
  
-   Mensajes de**WM\_HSCROLL** y de **WM\_VSCROLL** de las barras de desplazamiento relacionado \(vea a continuación\).  
  
-   **WM\_ACTIVATE** \(y **WM\_MDIACTIVATE** para MDI\) obtienen convertido en llamadas a la función virtual **CView::OnActivateView**.  
  
## Problemas de CMDIFrameWnd\/CMDIChildWnd  
 Ambos tipos de ventana de marco MDI derivan de **CFrameWnd** y por consiguiente se habilitan para la misma clase de enrutamiento de comandos y actualizar de la interfaz de usuario proporcionados en **CFrameWnd**.  En una aplicación típica de MDI, sólo la ventana de marco principal \(es decir, el objeto de **CMDIFrameWnd** \) contiene la barra de menús y la barra de estado y por consiguiente es el origen principal de la implementación del enrutamiento de comandos.  
  
 El esquema general de enrutamiento es que la ventana MDI secundaria de activo obtiene el primer acceso a comandos.  Las funciones de **PreTranslateMessage** predeterminado controlan las tablas del acelerador para las ventanas secundarias MDI \(primero\) y el marco MDI \(segundo\) así como los aceleradores de comando estándar del sistema de MDI controla normalmente por **TranslateMDISysAccel** \(último\).  
  
## Problemas de la barra de desplazamiento  
 Al administrar el desplazamiento\- mensaje \(**WM\_HSCROLL**\/**OnHScroll** y\/o **WM\_VSCROLL**\/**OnVScroll**\), debe intentar escribir el código del controlador de modo que no se basa en si el mensaje de la barra de desplazamiento procede.  Esto no es sólo un problema general de Windows, ya que los mensajes de desplazamiento pueden proceder de controles auténticos de la barra de desplazamiento o de las barras de desplazamiento de **WS\_HSCROLL**\/de**WS\_VSCROLL** que no son controles de barra de desplazamiento.  
  
 MFC extiende que al permitir a los controles de barra de desplazamiento son elementos secundarios o elementos relacionados de la ventana que se desplazados \(de hecho, la relación entre la barra de desplazamiento y la ventana de elemento primario\/secundario que es desplazados pueden ser nada\).  Esto es especialmente importante para las barras de desplazamiento compartidas con las ventanas divisoras.  Hace referencia a [Nota técnica 29](../mfc/tn029-splitter-windows.md) para obtener detalles sobre la implementación de **CSplitterWnd** incluidos más información sobre problemas compartidos de la barra de desplazamiento.  
  
 En un nota al margen, hay dos clases derivadas de **CWnd** donde los estilos de la barra de desplazamiento especificados en la hora de creación se interceptan y no se pasan a Windows.  Cuando se pasa a una rutina de creación, **WS\_HSCROLL** y **WS\_VSCROLL** se pueden establecer independientemente, pero después de la creación no se puede cambiar.  ¿Por supuesto, no debe comprobar o establecer directamente el WS\_? DESPLACE los bits de estilo de la ventana que crearon.  
  
 Para **CMDIFrameWnd** los estilos de la barra de desplazamiento que se pasa a **crear** o **LoadFrame** se utiliza para crear el MDICLIENT.  Si desea tener un área desplazable de MDICLIENT \(como el administrador de programa de Windows\) asegúrese de establecer ambos estilos de la barra de desplazamiento \(**WS\_HSCROLL** &#124; **WS\_VSCROLL**\) para el estilo usado para crear **CMDIFrameWnd**.  
  
 Para **CSplitterWnd** los estilos de la barra de desplazamiento se aplican a las barras de desplazamiento compartidas especiales regiones splitter.  Para las ventanas estáticas splitter, no establecerá normalmente los estilos de la barra de desplazamiento.  Para ventanas divisoras dinámicas, es normalmente tendrá el estilo de la barra de desplazamiento establecido en la dirección que se va a dividir, es decir, **WS\_HSCROLL** si puede dividir filas, **WS\_VSCROLL** si puede dividir columnas.  
  
## Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)