---
title: 'TN024: Mensajes y recursos definidos por MFC'
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.messages
helpviewer_keywords:
- resources [MFC]
- Windows messages [MFC], MFC-defined
- messages [MFC], MFC
- TN024
ms.assetid: c65353ce-8096-454b-ad22-1a7a1dd9a788
ms.openlocfilehash: 26f6effbafd8136661f0b1dc9a6b22138a23e547
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50639639"
---
# <a name="tn024-mfc-defined-messages-and-resources"></a>TN024: Mensajes y recursos definidos por MFC

> [!NOTE]
>  La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea. Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos. Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.

Esta nota describe los mensajes internos de Windows y los formatos de recursos utilizados por MFC. Esta información explica la implementación de framework y le ayudará a depurar la aplicación. El aventurero, aunque toda esta información es oficialmente compatible, puede usar parte de esta información para implementaciones avanzadas.

Esta nota contiene detalles de implementación privados de MFC; todo el contenido está sujeto a cambios en el futuro. Mensajes de Windows privados de MFC tienen un significado en el ámbito de una única solicitud pero cambiarán en el futuro para contener mensajes de todo el sistema.

Los mensajes de Windows privados de intervalo de MFC y los tipos de recursos están en el intervalo reservado "system" reservan por Microsoft Windows. Se usan en estos momentos no todos los números de los intervalos y, en el futuro, se pueden utilizar números nuevos en el intervalo. Se pueden cambiar los números de usados en esos momentos.

Windows privados de MFC los mensajes están en el intervalo 0x360 -> 0x37F.

Recurso privado MFC tipos están en el rango 0xF0 -> 0xFF.

**Mensajes de Windows privados de MFC**

Estos mensajes de Windows se usan en lugar de funciones virtuales de C++ donde se requiere relativamente el acoplamiento flexible entre los objetos de ventana y donde una función virtual de C++ no serían adecuada.

Estos mensajes de Windows privados y estructuras de parámetro asociado se declaran en el encabezado de MFC privada ' AFXPRIV. H'. Se avisará de que el código que incluye este encabezado puede depender de comportamiento no documentado y probablemente se interrumpirán en futuras versiones de MFC.

En el caso excepcional de que se necesitan controlar uno de estos mensajes, debe utilizar la macro de mapa de mensajes ON_MESSAGE y procesar el mensaje en el formato genérico de LRESULT/WPARAM y LPARAM.

**WM_QUERYAFXWNDPROC**

Este mensaje se envía a una ventana que se va a crear. Esto se envía una etapa muy temprana del proceso de creación como un método para determinar si es WndProc **AfxWndProc. AfxWndProc** devuelve 1.

|||
|-|-|
|wParam|No se utiliza|
|lParam|No se utiliza|
|devuelve|1 si se procesó **AfxWndProc**|

**WM_SIZEPARENT**

Este mensaje se envía una ventana de marco para sus elementos secundarios inmediatos durante el cambio de tamaño (`CFrameWnd::OnSize` llamadas `CFrameWnd::RecalcLayout` que llama a `CWnd::RepositionBars`) para volver a colocar las barras de control alrededor del lado del marco. La estructura AFX_SIZEPARENTPARAMS contiene el rectángulo de cliente disponibles actual del elemento primario y un HDWP (que puede ser NULL) con el que se va a llamar a `DeferWindowPos` para minimizar la actualización de la pantalla.

|||
|-|-|
|wParam|No se utiliza|
|lParam|Dirección de una estructura AFX_SIZEPARENTPARAMS|
|devuelve|No se utiliza (0)|

Omitiendo el mensaje indica que la ventana no participa en el diseño.

**WM_SETMESSAGESTRING**

Este mensaje se envía a una ventana de marco para solicitarle que actualice la línea de mensaje en la barra de estado. Puede ser un identificador de cadena o un LPCSTR especificada (pero no ambos).

|||
|-|-|
|wParam|Cadena de identificador (o cero)|
|lParam|LPCSTR para la cadena (o NULL)|
|devuelve|No se utiliza (0)|

**WM_IDLEUPDATECMDUI**

Este mensaje se envía en tiempo de inactividad para implementar la actualización de tiempo de inactividad de los controladores de interfaz de usuario de comando de actualización. Si la ventana (normalmente una barra de controles) controla el mensaje, crea un `CCmdUI` objeto (o un objeto de una clase derivada) y llamar a `CCmdUI::DoUpdate` para cada uno de los "elementos" en la ventana. Esto a su vez buscará un controlador ON_UPDATE_COMMAND_UI para los objetos de la cadena de controlador de comandos.

|||
|-|-|
|wParam|BOOL bDisableIfNoHandler|
|lParam|No se utiliza (0)|
|devuelve|No se utiliza (0)|

*bDisableIfNoHandler* es distinto de cero para deshabilitar el objeto de interfaz de usuario si hay un ON_UPDATE_COMMAND_UI ni un controlador ON_COMMAND.

**WM_EXITHELPMODE**

Este mensaje se registra en un `CFrameWnd` modo de ayuda que se va a salir sensible al contexto. La recepción de este mensaje termina el bucle modal iniciado por `CFrameWnd::OnContextHelp`.

|||
|-|-|
|wParam|No se utiliza (0)|
|lParam|No se utiliza (0)|
|devuelve|No se utiliza|

**WM_INITIALUPDATE**

Este mensaje se envía por la plantilla de documento a todos los descendientes de una ventana de marco cuándo es seguro para que puedan realizar su actualización inicial. Se asigna a una llamada a `CView::OnInitialUpdate` pero se puede usar en otros `CWnd`-las clases de otra actualización Monoestable derivadas.

|||
|-|-|
|wParam|No se utiliza (0)|
|lParam|No se utiliza (0)|
|devuelve|No se utiliza (0)|

**WM_RECALCPARENT**

Este mensaje se envía por una vista a su ventana primaria (obtenidos a través de `GetParent`) para forzar una actualización de diseño (normalmente, el elemento primario llamará `RecalcLayout`). Se utiliza en aplicaciones de servidor OLE cuando sea necesario para el marco aumentar de tamaño a medida que crece el tamaño total de la vista.

Si este mensaje procesa la ventana primaria debe devolver TRUE y rellenar la estructura de RECT pasado lParam con el nuevo tamaño del área cliente. Esto se usa en `CScrollView` administre correctamente los barras de desplazamiento (lugar, a continuación, en la parte exterior de la ventana cuando se agregan) cuando un objeto de servidor está activado en contexto.

|||
|-|-|
|wParam|No se utiliza (0)|
|lParam|LPRECT rectClient, puede ser NULL|
|devuelve|TRUE si el nuevo cliente rectángulo devuelto, FALSE en caso contrario|

**WM_SIZECHILD**

Este mensaje se envía por `COleResizeBar` a su ventana propietaria (a través de `GetOwner`) cuando el usuario cambia el tamaño de la barra de cambio de tamaño con los controladores de tamaño. `COleIPFrameWnd` responde a este mensaje al intentar cambiar la posición de la ventana de marco que el usuario ha solicitado.

El nuevo rectángulo, en coordenadas de cliente en relación con la ventana de marco que contiene la barra de cambio de tamaño, se apunta en lParam.

|||
|-|-|
|wParam|No se utiliza (0)|
|lParam|LPRECT rectNew|
|devuelve|No se utiliza (0)|

**WM_DISABLEMODAL**

Este mensaje se envía a todas las ventanas emergentes que pertenecen a una ventana de marco que se va a desactivar. La ventana de marco utiliza el resultado para determinar si se deben deshabilitar la ventana emergente.

Puede utilizarlo para realizar un procesamiento especial en la ventana emergente cuando el marco entra en un estado modal o para impedir que se va a deshabilitar determinadas ventanas emergentes. Información sobre herramientas usa este mensaje para que se destruyen cuando la ventana de marco entra en un estado modal, por ejemplo.

|||
|-|-|
|wParam|No se utiliza (0)|
|lParam|No se utiliza (0)|
|devuelve|Distinto de cero a **no** deshabilitar la ventana, 0 indica que la ventana se deshabilitará.|

**WM_FLOATSTATUS**

Este mensaje se envía a todas las ventanas emergentes propiedad de una ventana de marco cuando el marco se activa o desactivado por otra ventana del marco de nivel superior. Esto se usa la implementación de MFS_SYNCACTIVE en `CMiniFrameWnd`, para mantener la activación de estas ventanas emergentes en sincronización con la activación de la ventana de marco de nivel superior.

|||
|-|-|
|wParam|Es uno de los siguientes valores:<br /><br /> FS_SHOW<br /><br /> FS_HIDE<br /><br /> FS_ACTIVATE<br /><br /> FS_DEACTIVATE<br /><br /> FS_ENABLEFS_DISABLE<br /><br /> FS_SYNCACTIVE|
|lParam|No se utiliza (0)|

El valor devuelto debe ser distinto de cero si FS_SYNCACTIVE es conjunto y la ventana de sincroniza su activación con el marco primario. `CMiniFrameWnd` Devuelve distinto de cero cuando se establece el estilo en MFS_SYNCACTIVE.

Para obtener más información, vea la implementación de `CMiniFrameWnd`.

## <a name="wmactivatetoplevel"></a>WM_ACTIVATETOPLEVEL

Este mensaje se envía a una ventana de nivel superior cuando se activa o desactiva una ventana en su "grupo de nivel superior". Una ventana de forma parte de un grupo de nivel superior si es una ventana de nivel superior (ningún elemento primario o propietario), o sea propiedad de este tipo de ventana. Este mensaje es un uso similar a WM_ACTIVATEAPP, pero funciona en situaciones en que windows que pertenecen a diferentes procesos mixto en una jerarquía única ventana (habitual en aplicaciones OLE).

## <a name="wmcommandhelp-wmhelphittest-wmexithelpmode"></a>WM_EXITHELPMODE WM_COMMANDHELP, WM_HELPHITTEST,

Estos mensajes se utilizan en la implementación de la Ayuda contextual. Consulte [Nota técnica 28](../mfc/tn028-context-sensitive-help-support.md) para obtener más información.

## <a name="mfc-private-resource-formats"></a>Formatos de recursos privados de MFC

Actualmente, MFC define dos formatos de recurso privado: RT_TOOLBAR y RT_DLGINIT.

## <a name="rttoolbar-resource-format"></a>Formato del recurso RT_TOOLBAR

La barra de herramientas predeterminado proporcionado por el Asistente para aplicaciones se basa en un recurso personalizado RT_TOOLBAR, que se introdujo en 4.0 de MFC. Puede editar este recurso con el editor de la barra de herramientas.

## <a name="rtdlginit-resource-format"></a>Formato de recursos RT_DLGINIT

Un formato de los recursos privados de MFC se usa para almacenar información de inicialización del cuadro de diálogo adicional. Esto incluye las cadenas iniciales almacenadas en un cuadro combinado. El formato de este recurso no está diseñado para editarse manualmente, pero se controla mediante Visual C++.

Visual C++ y este recurso RT_DLGINIT no tienen que usar las características relacionadas de MFC, puesto que no hay alternativa al uso de la información en el recurso de la API. Uso de Visual C++ facilita mucho más fáciles de escribir, mantener y trasladar la aplicación a largo plazo.

La estructura básica de un recurso RT_DLGINIT es como sigue:

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

Una sección repetida contiene el identificador de control para enviar el mensaje, el mensaje # para enviar (un mensaje normal de Windows) y una longitud variable de datos. Se envía el mensaje de Windows en un formulario:

```
SendDlgItemMessage(<Control ID>, <Message #>, 0, &<Data>);
```

Se trata de un formato muy general, lo que permite los mensajes de Windows y el contenido de los datos. El editor de recursos de Visual C++ y MFC solo admiten un subconjunto limitado de mensajes de Windows: CB_ADDSTRING de las opciones de lista iniciales en los cuadros combinados (los datos son una cadena de texto).

## <a name="see-also"></a>Vea también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)

