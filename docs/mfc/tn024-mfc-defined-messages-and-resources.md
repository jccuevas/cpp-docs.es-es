---
title: 'TN024: Mensajes definidos por MFC y recursos | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.mfc.messages
dev_langs: C++
helpviewer_keywords:
- resources [MFC]
- Windows messages [MFC], MFC-defined
- messages [MFC], MFC
- TN024
ms.assetid: c65353ce-8096-454b-ad22-1a7a1dd9a788
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e3987f9716601eb45cd3043670b90f5e3ffd1be9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="tn024-mfc-defined-messages-and-resources"></a>TN024: Mensajes y recursos definidos por MFC
> [!NOTE]
>  La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea. Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos. Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.  
  
 Esta nota describe los mensajes internos de Windows y los formatos de recursos utilizados por MFC. Esta información explica la implementación de framework y te ayudará a depurar la aplicación. Para aventura, incluso aunque oficialmente no compatible, toda esta información se pueden utilizar algunas de esta información para implementaciones avanzadas.  
  
 Esta nota contiene detalles de la implementación privada de MFC; todo el contenido está sujeto a cambios en el futuro. Mensajes de Windows privados de MFC tienen un significado en el ámbito de una única solicitud pero cambiarán en el futuro para contener mensajes de todo el sistema.  
  
 Los mensajes de Windows privados de intervalo de MFC y los tipos de recursos están en el intervalo reservado "system" retirados por Microsoft Windows. Se usan actualmente no todos los números de los intervalos y, en el futuro, se pueden utilizar los nuevos números en el intervalo. Se pueden cambiar los números de usados en esos momentos.  
  
 MFC Windows privado mensajes están en el intervalo 0x360 -> 0x37F.  
  
 Recurso privado MFC tipos están en el rango 0xF0 -> 0xFF.  
  
 **Mensajes de Windows privados de MFC**  
  
 Estos mensajes de Windows se usan en lugar de funciones virtuales de C++, donde se requiere relativamente un acoplamiento entre los objetos de ventana y donde una función virtual de C++ no sería apropiada.  
  
 Estos mensajes de Windows privados y estructuras de parámetro asociados se declaran en el encabezado MFC privado ' AFXPRIV. H'. Le advertimos que cualquier código que incluye este encabezado puede basarse en un comportamiento no documentado y probablemente generará un error en futuras versiones de MFC.  
  
 En el caso excepcional de que se necesitan controlar uno de estos mensajes, debe usar el `ON_MESSAGE` macros de mapa de mensajes y procesar el mensaje en el formato LRESULT/WPARAM/LPARAM genérico.  
  
 **WM_QUERYAFXWNDPROC**  
  
 Este mensaje se envía a una ventana que se va a crear. Se envía como un método para determinar si la / / WndProc es muy pronto en el proceso de creación **AfxWndProc. AfxWndProc** devuelve 1.  
  
|||  
|-|-|  
|wParam|No se utiliza|  
|lParam|No se utiliza|  
|devuelve|Devuelve 1 si procesados por **AfxWndProc**|  
  
 **WM_SIZEPARENT**  
  
 Este mensaje se envía mediante una ventana de marco a sus elementos secundarios inmediatos durante el cambio de tamaño (**CFrameWnd::OnSize** llamadas `CFrameWnd::RecalcLayout` que llama `CWnd::RepositionBars`) para cambiar la posición de las barras de control alrededor del lado del marco. El **AFX_SIZEPARENTPARAMS** estructura contiene el rectángulo de cliente disponibles actual del elemento primario y un HDWP (que puede ser NULL) con el que se va a llamar a `DeferWindowPos` para minimizar la actualización de la pantalla.  
  
|||  
|-|-|  
|wParam|No se utiliza|  
|lParam|Dirección de un **AFX_SIZEPARENTPARAMS** estructura|  
|devuelve|No se utiliza (0)|  
  
 Omitiendo el mensaje indica que la ventana de no participar en el diseño.  
  
 **WM_SETMESSAGESTRING**  
  
 Este mensaje se envía a una ventana de marco para solicitarle que actualice la línea de mensaje en la barra de estado. Puede ser un identificador de cadena o un LPCSTR especificado (pero no ambos).  
  
|||  
|-|-|  
|wParam|Cadena de identificador (o cero)|  
|lParam|LPCSTR para la cadena (o NULL)|  
|devuelve|No se utiliza (0)|  
  
 **WM_IDLEUPDATECMDUI**  
  
 Este mensaje se envía en tiempo de inactividad para implementar la actualización de tiempo de inactividad de los controladores de interfaz de usuario de comando de actualización. Si la ventana (normalmente una barra de controles) controla el mensaje, crea un `CCmdUI` objeto (o un objeto de una clase derivada) y llame a **CCmdUI::DoUpdate** para cada uno de los "elementos" en la ventana. Esto comprobará a su vez un `ON_UPDATE_COMMAND_UI` controlador para los objetos de la cadena de controlador de comandos.  
  
|||  
|-|-|  
|wParam|BOOL bDisableIfNoHandler|  
|lParam|No se utiliza (0)|  
|devuelve|No se utiliza (0)|  
  
 *bDisableIfNoHandler* es distinto de cero para deshabilitar el objeto de interfaz de usuario si no hay ninguna de ellas una `ON_UPDATE_COMMAND_UI` ni un `ON_COMMAND` controlador.  
  
 **WM_EXITHELPMODE**  
  
 Este mensaje se registra en un `CFrameWnd` modo de ayuda que se va a salir sensible al contexto. La recepción de este mensaje finaliza el bucle modal iniciado por **CFrameWnd::OnContextHelp.**  
  
|||  
|-|-|  
|wParam|No se utiliza (0)|  
|lParam|No se utiliza (0)|  
|devuelve|No se utiliza|  
  
 **WM_INITIALUPDATE**  
  
 Este mensaje se envía por la plantilla de documento a todos los descendientes de una ventana de marco cuándo es seguro para llevar a cabo su actualización inicial. Se asigna a una llamada a `CView::OnInitialUpdate` pero se puede usar en otros `CWnd`-las clases para otro actualizar Monoestable derivadas.  
  
|||  
|-|-|  
|wParam|No se utiliza (0)|  
|lParam|No se utiliza (0)|  
|devuelve|No se utiliza (0)|  
  
 **WM_RECALCPARENT**  
  
 Este mensaje se envía por una vista a su ventana primaria (obtenidos mediante `GetParent`) para forzar una actualización de diseño (normalmente, el elemento primario llamará `RecalcLayout`). Se utiliza en aplicaciones de servidor OLE donde es necesario para el marco aumentando de tamaño a medida que aumenta el tamaño total de la vista.  
  
 Si la ventana primaria procesa este mensaje debe devolver TRUE y rellenar la estructura RECT pasada lParam con el nuevo tamaño del área cliente. Se utiliza en `CScrollView` administre correctamente las barras de desplazamiento (posición, a continuación, en la parte exterior de la ventana cuando se agregan) cuando un objeto de servidor está activado en el contexto.  
  
|||  
|-|-|  
|wParam|No se utiliza (0)|  
|lParam|LPRECT rectClient, puede ser NULL|  
|devuelve|TRUE si el nuevo cliente rectángulo devuelto, FALSE en caso contrario|  
  
 **WM_SIZECHILD**  
  
 Este mensaje se envía por `COleResizeBar` a su ventana propietaria (a través de `GetOwner`) cuando el usuario cambia el tamaño de la barra de cambio de tamaño con los controladores de tamaño. `COleIPFrameWnd`responde a este mensaje al intentar cambiar la posición de la ventana de marco tal y como se ha solicitado el usuario.  
  
 LParam apunta en el nuevo rectángulo, en coordenadas de cliente en relación con la ventana de marco que contiene la barra de cambio de tamaño.  
  
|||  
|-|-|  
|wParam|No se utiliza (0)|  
|lParam|LPRECT rectNew|  
|devuelve|No se utiliza (0)|  
  
 **WM_DISABLEMODAL**  
  
 Este mensaje se envía a todas las ventanas emergentes que pertenecen a una ventana de marco que se está desactivando. La ventana de marco, utiliza el resultado para determinar si se debe o no deshabilitar la ventana emergente.  
  
 Se puede usar para realizar un procesamiento especial en la ventana emergente cuando el marco entra en un estado modal o para impedir que determinadas ventanas emergentes obtener deshabilitado. Información sobre herramientas usa este mensaje por sí mismos destruir cuando la ventana de marco entra en un estado modal, por ejemplo.  
  
|||  
|-|-|  
|wParam|No se utiliza (0)|  
|lParam|No se utiliza (0)|  
|devuelve|Es distinto de cero para **no** deshabilitar la ventana, 0 indica que la ventana se deshabilitará.|  
  
 **WM_FLOATSTATUS**  
  
 Este mensaje se envía a todas las ventanas emergentes que pertenecen a una ventana de marco cuando el marco se activa o se desactiva por otra ventana de marco de nivel superior. Se utiliza la implementación de **MFS_SYNCACTIVE** en `CMiniFrameWnd`, para mantener la activación de estas ventanas emergentes sincronizadas con la activación de la ventana de marco de nivel superior.  
  
|||  
|-|-|  
|wParam|Es uno de los siguientes valores:<br /><br /> **FS_SHOW**<br /><br /> **FS_HIDE**<br /><br /> **FS_ACTIVATE**<br /><br /> **FS_DEACTIVATE**<br /><br /> **FS_ENABLEFS_DISABLE**<br /><br /> **FS_SYNCACTIVE**|  
|lParam|No se utiliza (0)|  
  
 El valor devuelto debe ser distinto de cero si **FS_SYNCACTIVE** está establecida y la ventana sincroniza su activación con el marco primario. `CMiniFrameWnd`Devuelve distinto de cero cuando se establece el estilo en **MFS_SYNCACTIVE.**  
  
 Para obtener más información, vea la implementación de `CMiniFrameWnd`.  
  
## <a name="wmactivatetoplevel"></a>WM_ACTIVATETOPLEVEL  
 Este mensaje se envía a una ventana de nivel superior cuando se activa o desactiva una ventana en su "grupo de nivel superior". Una ventana de forma parte de un grupo de nivel superior si es una ventana de nivel superior (no principal o propietaria) o pertenece a una de estas ventanas. Este mensaje es similar en uso para **WM_ACTIVATEAPP,** pero funciona en situaciones donde windows que pertenecen a procesos diferentes se combinan en una jerarquía de ventana única (habitual en aplicaciones OLE).  
  
## <a name="wmcommandhelp-wmhelphittest-wmexithelpmode"></a>WM_COMMANDHELP, WM_HELPHITTEST, WM_EXITHELPMODE  
 Estos mensajes se utilizan en la implementación de la Ayuda contextual. Consulte [28 de nota técnica](../mfc/tn028-context-sensitive-help-support.md) para obtener más información.  
  
## <a name="mfc-private-resource-formats"></a>Formatos de recursos privados de MFC  
 Actualmente, MFC define dos formatos de recurso privado: **RT_TOOLBAR** y **RT_DLGINIT**.  
  
## <a name="rttoolbar-resource-format"></a>Formato del recurso RT_TOOLBAR  
 La barra de herramientas predeterminado proporcionado por el Asistente para aplicaciones se basa en un **RT_TOOLBAR** recurso personalizado, que se introdujo en MFC 4.0. Puede editar este recurso mediante el editor de la barra de herramientas.  
  
## <a name="rtdlginit-resource-format"></a>Formato del recurso RT_DLGINIT  
 Un formato de recurso privado de MFC se utiliza para almacenar información de inicialización del cuadro de diálogo adicional. Esto incluye las cadenas iniciales que se almacena en un cuadro combinado. El formato de este recurso no está diseñado para editarse manualmente, pero sí se controla por Visual C++.  
  
 Visual C++ y esto **RT_DLGINIT** recurso no son necesarios para usar las características relacionadas de MFC, dado que hay alternativa de API a según se indica en el recurso. Con Visual C++ hace mucho más fáciles de escribir, mantener y traducir la aplicación a largo plazo.  
  
 La estructura básica de un **RT_DLGINIT** recursos es como sigue:  
  
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
  
 Una sección repetida contiene el identificador de control para enviar el mensaje, el mensaje # para envío (un mensaje normal de Windows) y una longitud variable de datos. En un formulario se envía el mensaje de Windows:  
  
```  
SendDlgItemMessage(<Control ID>, <Message #>, 0, &<Data>);
```  
  
 Se trata de un formato muy general, que permite a los mensajes de Windows y el contenido de los datos. El editor de recursos de Visual C++ y MFC solo admiten un subconjunto limitado de mensajes de Windows: CB_ADDSTRING de las opciones de lista iniciales para los cuadros combinados (los datos son una cadena de texto).  
  
## <a name="see-also"></a>Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)

