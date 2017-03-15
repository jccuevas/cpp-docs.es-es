---
title: "TN024: Mensajes y recursos definidos por MFC | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.messages"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "mensajes [C++], MFC"
  - "recursos [MFC]"
  - "TN024"
  - "mensajes de Windows [C++], definidos por MFC"
ms.assetid: c65353ce-8096-454b-ad22-1a7a1dd9a788
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# TN024: Mensajes y recursos definidos por MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea.  Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos.  Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.  
  
 Esta nota describe los mensajes de Windows y formatos internos de recursos utilizados por MFC.  Esta información se explica la implementación de .NET framework, y le ayudará a depurar la aplicación.  Para el aventurero, aunque toda esta información se oficialmente no compatibles, puede utilizar parte de esta información para las implementaciones avanzadas.  
  
 Esta nota contiene los detalles de implementación privado de MFC; todos los contenido está sujeto a cambios en el futuro.  Los mensajes privados de MFC Windows tienen significado en el ámbito de una aplicación solo pero se cambiarán en el futuro para contener mensajes sistema\- anchos.  
  
 El intervalo de mensajes privados de MFC Windows y los tipos de recursos están en el intervalo reservado “system” título a un lado por Microsoft Windows.  No todos los números de intervalos se utilizan actualmente y, en el futuro, los nuevos números en el intervalo se pueden utilizar.  Los números actualmente utilizados pueden cambiar.  
  
 Los mensajes privados de MFC Windows están en el intervalo 0x360\-0x37F\>.  
  
 Los tipos de recursos privados de MFC están en el intervalo 0xF0\-0xFF\>.  
  
 **Mensajes privados de MFC Windows**  
  
 Estos mensajes de Windows se utilizan en lugar de las funciones virtuales de C\+\+ donde vinculación relativamente independiente se requiere entre los objetos de la ventana y donde no es adecuada la función virtual de c\+\+.  
  
 Estos mensajes privados de Windows y estructuras asociadas de parámetros se declaran en el encabezado privado “AFXPRIV.H” MFC.  Adviértase que el código cualquiera de los que incluye este encabezado puede confiar en comportamiento indocumentado y adaptará probablemente versiones futuras de MFC.  
  
 En el caso necesario poco controlar uno de estos mensajes, debe utilizar la macro de mapa de mensajes de `ON_MESSAGE` y procesar el mensaje en formato genérico de LRESULT\/WPARAM\/LPARAM.  
  
 **WM\_QUERYAFXWNDPROC**  
  
 Este mensaje se envía a una ventana se está creando.  Esto se envía prematura del proceso de creación como método de determinar si el WndProc es **AfxWndProc. AfxWndProc** devuelve 1.  
  
|||  
|-|-|  
|wParam|No se utiliza|  
|lParam|No se utiliza|  
|devuelve|1 si es procesado por **AfxWndProc**|  
  
 **WM\_SIZEPARENT**  
  
 Este mensaje es enviado por una ventana de marco a sus elementos secundarios inmediatos durante el tamaño \(**CFrameWnd::OnSize** llama `CFrameWnd::RecalcLayout` que llama a `CWnd::RepositionBars`\) para colocar las barras de control de nuevo al lado del marco.  La estructura de **AFX\_SIZEPARENTPARAMS** contiene el rectángulo disponibles actual del elemento primario y un HDWP \(que puede ser NULL\) que para llamar a `DeferWindowPos` para minimizar la repintura.  
  
|||  
|-|-|  
|wParam|No se utiliza|  
|lParam|Dirección de una estructura de **AFX\_SIZEPARENTPARAMS**|  
|devuelve|No utilizado \(0\)|  
  
 Omitir el mensaje indica que la ventana no participa en el diseño.  
  
 **WM\_SETMESSAGESTRING**  
  
 Este mensaje se envía a una ventana de marco que solicita que actualice la línea de mensajes en la barra de estado.  Un identificador de cadena o un LPCSTR puede especificar \(pero no ambos\).  
  
|||  
|-|-|  
|wParam|Identificador de cadena \(o ninguno\)|  
|lParam|LPCSTR para la cadena \(o NULL\)|  
|devuelve|No utilizado \(0\)|  
  
 **WM\_IDLEUPDATECMDUI**  
  
 Este mensaje se envía en tiempo de inactividad para implementar la actualización del tiempo de inactividad de los controladores de la interfaz de usuario de actualización\- comando.  Si la ventana \(normalmente una barra de controles\) controla el mensaje, crea un objeto de `CCmdUI` \(o un objeto de una clase derivada\) y la llamada **CCmdUI::DoUpdate** para cada uno de los “elementos” en la ventana.  Esto a su vez comprobará si hay un controlador de `ON_UPDATE_COMMAND_UI` para los objetos en la cadena de comando\- controlador.  
  
|||  
|-|-|  
|wParam|BDisableIfNoHandler de BOOL|  
|lParam|No utilizado \(0\)|  
|devuelve|No utilizado \(0\)|  
  
 *el bDisableIfNoHandler* es distinto de cero deshabilitar el objeto de interfaz de usuario si hay ni `ON_UPDATE_COMMAND_UI` o controlador de `ON_COMMAND` .  
  
 **WM\_EXITHELPMODE**  
  
 Este mensaje se envía a `CFrameWnd` que salir del modo de ayuda contextual.  El mensaje de este mensaje finalizará el bucle modal iniciado por **CFrameWnd::OnContextHelp.**  
  
|||  
|-|-|  
|wParam|No utilizado \(0\)|  
|lParam|No utilizado \(0\)|  
|devuelve|No se utiliza|  
  
 **WM\_INITIALUPDATE**  
  
 Este mensaje es enviado por la plantilla de documento todos los descendientes de una ventana de marco cuando es seguro que hace la actualización inicial.  Asigna a una llamada a `CView::OnInitialUpdate` pero se puede utilizar en otro `CWnd`\- clases derivadas para otro actualizar paso a paso.  
  
|||  
|-|-|  
|wParam|No utilizado \(0\)|  
|lParam|No utilizado \(0\)|  
|devuelve|No utilizado \(0\)|  
  
 **WM\_RECALCPARENT**  
  
 Este mensaje es enviado por una vista a su ventana primaria \(obtenida mediante `GetParent`\) para forzar un cálculo de diseño \(normalmente, el elemento primario a `RecalcLayout`\).  Se utiliza en aplicaciones de servidor OLE donde es necesario que el cuadro aumenta de tamaño como el tamaño total de la vista crece.  
  
 Si la ventana primaria procesa este mensaje debe devolver TRUE y rellenar el RECT pasado en lParam con el nuevo tamaño del área de cliente.  Se utiliza en `CScrollView` para controlar correctamente las barras de desplazamiento \(place a fuera de la ventana cuando se agregan\) cuando un objeto de servidor es en contexto elevado.  
  
|||  
|-|-|  
|wParam|No utilizado \(0\)|  
|lParam|LPRECT rectClient, puede ser NULL|  
|devuelve|TRUE si el nuevo rectángulo de cliente que de lo contrario, es FALSE|  
  
 **WM\_SIZECHILD**  
  
 Este mensaje es enviado por `COleResizeBar` a su ventana propietaria \(mediante `GetOwner`\) cuando el usuario cambia el tamaño de la barra de tamaño con los controladores de tamaño.  `COleIPFrameWnd` responde a este mensaje intenta colocar la ventana cuadro de nuevo que el usuario ha solicitado.  
  
 El nuevo rectángulo, especificado en cliente coordina en relación con la ventana de marco que contiene la barra de tamaño, está señalado por el lParam.  
  
|||  
|-|-|  
|wParam|No utilizado \(0\)|  
|lParam|RectNew de LPRECT|  
|devuelve|No utilizado \(0\)|  
  
 **WM\_DISABLEMODAL**  
  
 Este mensaje se envía a todas las ventanas emergentes que pertenecen a una ventana de marco se desactivando que.  La ventana de marco utiliza el resultado para determinar si deshabilitar la ventana emergente.  
  
 Puede utilizar esto para realizar el procesamiento especial en la ventana emergente cuando el cuadro entra en un estado modal o mantener algunas ventanas emergentes de obtener deshabilitadas.  La información sobre herramientas usan este mensaje para destruirse cuando la ventana de marco entra en un estado modal, por ejemplo.  
  
|||  
|-|-|  
|wParam|No utilizado \(0\)|  
|lParam|No utilizado \(0\)|  
|devuelve|Distinto de cero a **NO** deshabilite la ventana, 0 indica que la ventana se deshabilitará|  
  
 **WM\_FLOATSTATUS**  
  
 Este mensaje se envía a todas las ventanas emergentes que pertenecen a una ventana de marco cuando el cuadro es activado o desactivado por otra ventana de nivel superior del cuadro.  Esto es utilizada por la implementación de **MFS\_SYNCACTIVE** en `CMiniFrameWnd`, para conservar la activación de estas ventanas emergentes en sincronización con la activación de la ventana de marco de nivel superior.  
  
|||  
|-|-|  
|wParam|Es uno de los valores siguientes:<br /><br /> **FS\_SHOW**<br /><br /> **FS\_HIDE**<br /><br /> **FS\_ACTIVATE**<br /><br /> **FS\_DEACTIVATE**<br /><br /> **FS\_ENABLEFS\_DISABLE**<br /><br /> **FS\_SYNCACTIVE**|  
|lParam|No utilizado \(0\)|  
  
 El valor devuelto debe ser distinto de cero si **FS\_SYNCACTIVE** es determinado y la ventana syncronizes la activación con marco primario.  `CMiniFrameWnd` devuelve cero cuando el estilo se establece en **MFS\_SYNCACTIVE.**  
  
 Para obtener más información, vea la implementación de `CMiniFrameWnd`.  
  
## WM\_ACTIVATETOPLEVEL  
 Este mensaje se envía a una ventana de nivel superior cuando una ventana en su “grupo de nivel superior” se activa o desactiva.  Una ventana es parte de un grupo de nivel superior si es una ventana de nivel superior \(ningún elemento primario o propietario\), o es propiedad de una ventana.  Este mensaje está en uso similar a **WM\_ACTIVATEAPP,** pero funciona en situaciones en las ventanas que pertenecen a procesos diferentes se mezclan en una única jerarquía de la ventana \(común en aplicaciones OLE\).  
  
## WM\_COMMANDHELP, WM\_HELPHITTEST, WM\_EXITHELPMODE  
 Estos mensajes se utilizan en la implementación de ayuda contextual.  Hace referencia a [Nota técnica 28](../mfc/tn028-context-sensitive-help-support.md) para obtener más información.  
  
## Formatos privados de MFC  
 Actualmente, MFC define dos formatos de recursos privadas: **RT\_TOOLBAR** y **RT\_DLGINIT**.  
  
## Formato de recursos de RT\_TOOLBAR  
 La barra de herramientas predeterminada proporcionada por AppWizard se basa en un recurso personalizado de **RT\_TOOLBAR** , introducido en MFC 4,0.  Puede modificar a este recurso mediante el editor de barras de herramientas.  
  
## Formato de recursos de RT\_DLGINIT  
 Un formato privado del recurso de MFC se utiliza para almacenar información de inicialización del diálogo.  Esto incluye cadenas iniciales almacenadas en un cuadro combinado.  El formato de este recurso no está diseñado para ser editado manualmente, pero es administrado por Visual C\+\+.  
  
 No requieren Visual C\+\+ y a este recurso de **RT\_DLGINIT** utilizar características relacionadas de MFC puesto que hay alternativa de API a utilizar la información en el recurso.  Con Visual C\+\+ facilita escribir, mantener convertir, y la aplicación a largo plazo.  
  
 La estructura básica de un recurso de **RT\_DLGINIT** es la siguiente:  
  
```  
+---------------+                    \  
| Control ID    |   UINT             |  
+---------------+                    |  
| Message #     |   UINT             |  
+---------------+                    |  
|length of data |   DWORD            |  
+---------------+                    |   Repeated  
|   Data        |   Variable Length  |   for each control  
|   ...         |   and Format       |   and message  
+---------------+                    /  
|     0         |   BYTE  
+---------------+  
```  
  
 Una sección repetida contiene el identificador del control para enviar el mensaje a, el mensaje \# enviar \(un mensaje de las ventanas normales\) y un de longitud variable de datos.  El mensaje de Windows se envía en un formulario:  
  
```  
SendDlgItemMessage(<Control ID>, <Message #>, 0, &<Data>);  
```  
  
 Esto es un formato muy general, permitiendo los mensajes de Windows y contenido de datos.  El editor de recursos y MFC de Visual C\+\+ solo admiten un subconjunto limitado de mensajes de Windows: CB\_ADDSTRING para las lista\- opciones iniciales para cuadros combinados \(datos es una cadena de texto\).  
  
## Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)