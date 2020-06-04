---
title: 'TN024: Mensajes y recursos definidos por MFC'
ms.date: 11/04/2016
helpviewer_keywords:
- resources [MFC]
- Windows messages [MFC], MFC-defined
- messages [MFC], MFC
- TN024
ms.assetid: c65353ce-8096-454b-ad22-1a7a1dd9a788
ms.openlocfilehash: 24bcacd46b839babe9c9c89facb1cc56d18c0ee5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370351"
---
# <a name="tn024-mfc-defined-messages-and-resources"></a>TN024: Mensajes y recursos definidos por MFC

> [!NOTE]
> La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea. Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos. Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.

Esta nota describe los mensajes internos de Windows y los formatos de recursos utilizados por MFC. Esta información explica la implementación del marco de trabajo y le ayudará a depurar la aplicación. Para los aventureros, aunque toda esta información no es oficialmente compatible, puede utilizar parte de esta información para implementaciones avanzadas.

Esta nota contiene detalles de implementación privada de MFC; todos los contenidos están sujetos a cambios en el futuro. Los mensajes de Windows privados de MFC tienen significado en el ámbito de una sola aplicación, pero cambiarán en el futuro para contener mensajes de todo el sistema.

El intervalo de mensajes y tipos de recursos privados de MFC Windows se encuentra en el intervalo "sistema" reservado reservado por Microsoft Windows. Actualmente no se utilizan todos los números en los rangos y, en el futuro, se pueden utilizar nuevos números en el rango. Los números utilizados actualmente pueden ser cambiados.

Los mensajes de Windows privados de MFC están en el intervalo 0x360->0x37F.

Los tipos de recursos privados de MFC están en el intervalo 0xF0->0xFF.

**Mensajes de Windows privados de MFC**

Estos mensajes de Windows se utilizan en lugar de funciones virtuales C++ donde se requiere un acoplamiento relativamente flojo entre los objetos de ventana y donde una función virtual C++ no sería adecuada.

Estos mensajes privados de Windows y las estructuras de parámetros asociadas se declaran en el encabezado privado MFC 'AFXPRIV. H'. Tenga en cuenta que cualquier código que incluya este encabezado puede depender del comportamiento no documentado y probablemente se interrumpirá en versiones futuras de MFC.

En el raro caso de que necesite controlar uno de estos mensajes, debe utilizar la macro de mapa de mensajes ON_MESSAGE y controlar el mensaje en el formato genérico LRESULT/WPARAM/LPARAM.

**WM_QUERYAFXWNDPROC**

Este mensaje se envía a una ventana que se está creando. Esto se envía muy temprano en el proceso de creación como un método para determinar si wndProc es **AfxWndProc. AfxWndProc** devuelve 1.

|||
|-|-|
|wParam|No se usa|
|lParam|No se usa|
|devuelve|1 si es procesado por **AfxWndProc**|

**WM_SIZEPARENT**

Este mensaje se envía mediante una ventana de marco`CFrameWnd::OnSize` `CFrameWnd::RecalcLayout` a `CWnd::RepositionBars`sus elementos secundarios inmediatos durante el cambio de tamaño (llamadas que llama) para cambiar la posición de las barras de control alrededor del lado del marco. La estructura AFX_SIZEPARENTPARAMS contiene el rectángulo de cliente disponible actual del elemento primario `DeferWindowPos` y un HDWP (que puede ser NULL) con el que llamar para minimizar el repintado.

|||
|-|-|
|wParam|No se usa|
|lParam|Dirección de una estructura AFX_SIZEPARENTPARAMS|
|devuelve|No utilizado (0)|

Ignorar el mensaje indica que la ventana no participa en el diseño.

**WM_SETMESSAGESTRING**

Este mensaje se envía a una ventana de marco para pedirle que actualice la línea del mensaje en la barra de estado. Se puede especificar un ID de cadena o un LPCSTR (pero no ambos).

|||
|-|-|
|wParam|ID de cadena (o cero)|
|lParam|LPCSTR para la cadena (o NULL)|
|devuelve|No utilizado (0)|

**WM_IDLEUPDATECMDUI**

Este mensaje se envía en tiempo de inactividad para implementar la actualización en tiempo de inactividad de los controladores de interfaz de usuario de comando de actualización. Si la ventana (normalmente una barra de `CCmdUI` control) controla el mensaje, crea `CCmdUI::DoUpdate` un objeto (o un objeto de una clase derivada) y llama a cada uno de los "elementos" de la ventana. Esto, a su vez, comprobará si hay un controlador de ON_UPDATE_COMMAND_UI para los objetos de la cadena de controlador de comandos.

|||
|-|-|
|wParam|BOOL bDisableIfNoHandler|
|lParam|No utilizado (0)|
|devuelve|No utilizado (0)|

*bDisableIfNoHandler* es distinto de cero para deshabilitar el objeto de interfaz de usuario si no hay ni un ON_UPDATE_COMMAND_UI ni un controlador de ON_COMMAND.

**WM_EXITHELPMODE**

Este mensaje se publica `CFrameWnd` en un que para salir del modo de ayuda sensible al contexto. La recepción de este mensaje finaliza `CFrameWnd::OnContextHelp`el bucle modal iniciado por .

|||
|-|-|
|wParam|No utilizado (0)|
|lParam|No utilizado (0)|
|devuelve|No se usa|

**WM_INITIALUPDATE**

La plantilla de documento envía este mensaje a todos los descendientes de una ventana de marco cuando es seguro para ellos realizar su actualización inicial. Se asigna a `CView::OnInitialUpdate` una llamada a `CWnd`pero se puede utilizar en otras clases derivadas para otra actualización de un solo disparo.

|||
|-|-|
|wParam|No utilizado (0)|
|lParam|No utilizado (0)|
|devuelve|No utilizado (0)|

**WM_RECALCPARENT**

Este mensaje se envía mediante una vista a `GetParent`su ventana primaria (obtenida a través `RecalcLayout`de ) para forzar un recálculo de diseño (normalmente, el elemento primario llamará). Esto se utiliza en aplicaciones de servidor OLE donde es necesario que el marco crezca en tamaño a medida que crece el tamaño total de la vista.

Si la ventana primaria procesa este mensaje, debe devolver TRUE y rellenar el RECT pasado en lParam con el nuevo tamaño del área de cliente. Esto se `CScrollView` utiliza para controlar correctamente los barras de desplazamiento (colocar a continuación en el exterior de la ventana cuando se agregan) cuando se activa un objeto de servidor en contexto.

|||
|-|-|
|wParam|No utilizado (0)|
|lParam|LPRECT rectClient, puede ser NULL|
|devuelve|TRUESi se devuelve un nuevo rectángulo de cliente, FALSE en caso contrario|

**WM_SIZECHILD**

Este mensaje se `COleResizeBar` envía a su `GetOwner`ventana propietaria (a través de ) cuando el usuario cambia el tamaño de la barra de cambio de tamaño con los identificadores de cambio de tamaño. `COleIPFrameWnd`responde a este mensaje intentando cambiar la posición de la ventana de marco como el usuario ha solicitado.

El nuevo rectángulo, dado en las coordenadas de cliente en relación con la ventana de marco que contiene la barra de cambio de tamaño, es señalado por lParam.

|||
|-|-|
|wParam|No utilizado (0)|
|lParam|LPRECT rectNew|
|devuelve|No utilizado (0)|

**WM_DISABLEMODAL**

Este mensaje se envía a todas las ventanas emergentes propiedad de una ventana de marco que se está desactivando. La ventana de marco utiliza el resultado para determinar si se debe deshabilitar o no la ventana emergente.

Puede utilizar esto para realizar un procesamiento especial en la ventana emergente cuando el marco entra en un estado modal o para evitar que ciertas ventanas emergentes se deshabiliten. La información sobre herramientas utiliza este mensaje para destruirse a sí mismos cuando la ventana de marco entra en un estado modal, por ejemplo.

|||
|-|-|
|wParam|No utilizado (0)|
|lParam|No utilizado (0)|
|devuelve|No cero para **NO** desactivar la ventana, 0 indica que la ventana se desactivará|

**WM_FLOATSTATUS**

Este mensaje se envía a todas las ventanas emergentes propiedad de una ventana de marco cuando el marco está activado o desactivado por otra ventana de marco de nivel superior. Esto es utilizado por la `CMiniFrameWnd`implementación de MFS_SYNCACTIVE en , para mantener la activación de estas ventanas emergentes en sincronía con la activación de la ventana de marco de nivel superior.

|||
|-|-|
|wParam|Es uno de los siguientes valores:<br /><br /> FS_SHOW<br /><br /> FS_HIDE<br /><br /> FS_ACTIVATE<br /><br /> FS_DEACTIVATE<br /><br /> FS_ENABLEFS_DISABLE<br /><br /> FS_SYNCACTIVE|
|lParam|No utilizado (0)|

El valor devuelto debe ser distinto de cero si se establece FS_SYNCACTIVE y la ventana sincroniza su activación con el marco primario. `CMiniFrameWnd`devuelve distinto de cero cuando el estilo se establece en MFS_SYNCACTIVE.

Para obtener más información, `CMiniFrameWnd`consulte la implementación de .

## <a name="wm_activatetoplevel"></a>WM_ACTIVATETOPLEVEL

Este mensaje se envía a una ventana de nivel superior cuando una ventana de su "grupo de nivel superior" está activada o desactivada. Una ventana forma parte de un grupo de nivel superior si es una ventana de nivel superior (sin elemento primario o propietario), o es propiedad de dicha ventana. Este mensaje es similar en uso a WM_ACTIVATEAPP, pero funciona en situaciones donde las ventanas que pertenecen a diferentes procesos se mezclan en una jerarquía de ventana única (común en aplicaciones OLE).

## <a name="wm_commandhelp-wm_helphittest-wm_exithelpmode"></a>WM_COMMANDHELP, WM_HELPHITTEST, WM_EXITHELPMODE

Estos mensajes se utilizan en la implementación de la Ayuda contextual. Consulte [la Nota técnica 28](../mfc/tn028-context-sensitive-help-support.md) para obtener más información.

## <a name="mfc-private-resource-formats"></a>Formatos de recursos privados MFC

Actualmente, MFC define dos formatos de recursos privados: RT_TOOLBAR y RT_DLGINIT.

## <a name="rt_toolbar-resource-format"></a>Formato de RT_TOOLBAR recursos

La barra de herramientas predeterminada proporcionada por AppWizard se basa en un RT_TOOLBAR recurso personalizado, que se introdujo en MFC 4.0. Puede editar este recurso mediante el editor de la barra de herramientas.

## <a name="rt_dlginit-resource-format"></a>Formato de RT_DLGINIT recursos

Un formato de recurso privado MFC se utiliza para almacenar información de inicialización de cuadro de diálogo adicional. Esto incluye las cadenas iniciales almacenadas en un cuadro combinado. El formato de este recurso no está diseñado para editarse manualmente, pero visual C++.

Visual C++ y este recurso de RT_DLGINIT no son necesarios para usar las características relacionadas de MFC, ya que hay alternativa de API al uso de la información en el recurso. El uso de Visual C++ facilita mucho la escritura, el mantenimiento y la traducción de la aplicación a largo plazo.

La estructura básica de un recurso RT_DLGINIT es la siguiente:

```
+---------------+    \
| Control ID    |   UINT             |
+---------------+    |
| Message #     |   UINT             |
+---------------+    |
|length of data |   DWORD            |
+---------------+    |   Repeated
|   Data        |   Variable Length  |   for each control
|   ...         |   and Format       |   and message
+---------------+    /
|     0         |   BYTE
+---------------+
```

Una sección repetida contiene el identificador de control al que se enviará el mensaje, el mensaje a enviar (un mensaje normal de Windows) y una longitud variable de datos. El mensaje de Windows se envía en un formulario:

```
SendDlgItemMessage(<Control ID>, <Message #>, 0, &<Data>);
```

Este es un formato muy general, permitiendo cualquier mensaje de Windows y contenido de datos. El editor de recursos de Visual C++ y MFC solo admiten un subconjunto limitado de mensajes de Windows: CB_ADDSTRING para las opciones de lista iniciales para cuadros combinados (los datos son una cadena de texto).

## <a name="see-also"></a>Consulte también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)
