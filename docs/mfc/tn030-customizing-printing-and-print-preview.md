---
title: "TN030: Personalizar la impresión y vista previa de impresión | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.print
dev_langs: C++
helpviewer_keywords:
- TN030
- customizing printing and print preview
- printing [MFC], views
- printing views [MFC]
- print preview [MFC], customizing
ms.assetid: 32744697-c91c-41b6-9a12-b8ec01e0d438
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: aa11c30fb41630a5b293698fe3e69a80509f3f2f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="tn030-customizing-printing-and-print-preview"></a>TN030: Personalizar la impresión y la vista previa de impresión
> [!NOTE]
>  La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea. Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos. Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.  
  
 Esta nota describe el proceso de personalización de vista previa de impresión y y describe los fines de las rutinas de devolución de llamada que se usa en `CView` y las rutinas de devolución de llamada y las funciones miembro de **CPreviewView**.  
  
## <a name="the-problem"></a>El problema  
 MFC proporciona una solución completa para la mayoría de impresión y vista previa de impresión es necesario. En la mayoría de los casos, es necesario tener una vista que se puede imprimir y obtener una vista previa poco código adicional. Sin embargo, hay maneras de optimizar la impresión que requieren un esfuerzo significativo por parte del desarrollador y algunas aplicaciones necesitan agregar elementos de la interfaz de usuario específico para el modo de vista previa de impresión.  
  
## <a name="efficient-printing"></a>Impresión eficaz  
 Cuando una aplicación MFC se imprime utilizando los métodos estándar, Windows dirige todas las llamadas de salida de interfaz de dispositivo gráfico (GDI) a un metarchivo en memoria. Cuando `EndPage` es llama, Windows reproduce el metarchivo una vez para cada banda físico que requiere la impresora para imprimir una página. Durante esta representación GDI consulta con frecuencia el procedimiento anular para determinar si debe continuar. Por lo general, el procedimiento de anulación permite mensajes ser procesado por lo que el usuario puede anular el trabajo de impresión mediante un cuadro de diálogo de impresión.  
  
 Desgraciadamente, esto puede ralentizar el proceso de impresión. Si la impresión de la aplicación debe ser más rápida que puede lograrse mediante la técnica estándar, debe implementar bandas manual.  
  
## <a name="print-banding"></a>Imprimir bandas  
 Con el fin de orígenes externos manualmente, debe volver implementar el bucle de impresión que `OnPrint` se llama varias veces por página (una por cada banda). El bucle de impresión se implementa en el **OnFilePrint** función en viewprnt.cpp. En su `CView`-clase derivada, se sobrecarga esta función para que la entrada de mapa de mensajes para controlar el comando de impresión llama a la función de impresión. Copia la **OnFilePrint** rutina y cambie el bucle de impresión para implementar bandas. Probablemente también desee pasar el rectángulo bandas a las funciones de impresión para que se puede optimizar el dibujo basado en la sección de la página que se pueda imprimir.  
  
 En segundo lugar, se debe llamar con frecuencia `QueryAbort` mientras se dibuja la banda. En caso contrario, no se llamará al procedimiento anular y el usuario pueda cancelar el trabajo de impresión.  
  
## <a name="print-preview-electronic-paper-with-user-interface"></a>Vista previa de impresión: Papel electrónico con una interfaz de usuario  
 Vista preliminar, en esencia, intente apagar la pantalla en una emulación de una impresora. De forma predeterminada, el área de cliente de la ventana principal se utiliza para mostrar una o dos páginas completamente dentro de la ventana. El usuario es capaz de usar el zoom en un área de la página para ver con más detalle. Con compatibilidad adicional, el usuario puede incluso podrá editar el documento en modo de vista previa.  
  
## <a name="customizing-print-preview"></a>Personalizar la vista previa de impresión  
 Esta nota solo se ocupa de uno de los aspectos de la modificación de la vista previa de impresión: adición de interfaz de usuario en modo de vista previa. Otras modificaciones son posibles, pero dichos cambios están fuera del ámbito de este contenido.  
  
## <a name="to-add-ui-to-the-preview-mode"></a>Para agregar la interfaz de usuario para el modo de vista previa  
  
1.  Derivar una clase de vista de **CPreviewView**.  
  
2.  Agregar controladores de comandos para los aspectos de la interfaz de usuario que desee.  
  
3.  Si va a agregar aspectos visuales a la pantalla, invalidar `OnDraw` y realizar el dibujo después de llamar a **CPreviewView::OnDraw.**  
  
## <a name="onfileprintpreview"></a>OnFilePrintPreview  
 Este es el controlador de comandos para la vista previa de impresión. La implementación predeterminada es:  
  
```  
void CView::OnFilePrintPreview()  
{ *// In derived classes,
    implement special window handling here *// Be sure to Unhook Frame Window close if hooked.  
 *// must not create this on the frame. Must outlive this function  
    CPrintPreviewState* pState = new CPrintPreviewState;  
 
    if (!DoPrintPreview(AFX_IDD_PREVIEW_TOOLBAR,
    this,  
    RUNTIME_CLASS(CPreviewView),
    pState))  
 { *// In derived classes,
    reverse special window handling *// here for Preview failure case  
 
    TRACE0("Error: DoPrintPreview failed");

    AfxMessageBox(AFX_IDP_COMMAND_FAILURE);

 delete pState;      // preview failed to initialize, *// delete State now  
 }  
}  
```  
  
 **DoPrintPreview** ocultará el panel principal de la aplicación. Barras de control, como la barra de estado, se pueden conservar especificándolas en el pState ->**dwStates** miembro (se trata de una máscara de bits y los bits de barras de controles individuales se definen mediante **AFX_CONTROLBAR_MASK**(AFX_IDW_MYBAR)). La ventana pState ->**nIDMainPane** es la ventana que se oculta automáticamente y reshown. **DoPrintPreview** , a continuación, creará una barra de botones de la interfaz de usuario estándar de vista previa. Si se necesita control de ventana especial, como ocultar o mostrar otras ventanas, que deben realizarse antes de **DoPrintPreview** se llama.  
  
 De forma predeterminada, cuando finaliza la vista previa de impresión, devuelve las barras de control a su estado original y el panel principal a visible. Si es necesario un tratamiento especial, se debe hacer en un reemplazo del **EndPrintPreview.** Si **DoPrintPreview** se produce un error, también proporcionan un tratamiento especial.  
  
 Se llama a DoPrintPreview con:  
  
-   El identificador de recurso de la plantilla de cuadro de diálogo para la barra de herramientas de vista previa.  
  
-   Un puntero a la vista para realizar la impresión de la vista previa de impresión.  
  
-   La clase en tiempo de ejecución de la clase de vista previa. Esto se creará dinámicamente en DoPrintPreview.  
  
-   El puntero CPrintPreviewState. Tenga en cuenta que la estructura de CPrintPreviewState (o la estructura derivada si la aplicación necesita más estado conservado) debe *no* crearse en el marco. DoPrintPreview es no modal y esta estructura debe sobreviven hasta que se llama EndPrintPreview.  
  
    > [!NOTE]
    >  Si se necesita una vista independiente o una clase de vista de compatibilidad con la impresión, se debe pasar un puntero a ese objeto como el segundo parámetro.  
  
## <a name="endprintpreview"></a>EndPrintPreview  
 Esto se llama para finalizar el modo de vista previa de impresión. A menudo es conveniente pasar a la página en el documento que se mostró por última vez en vista previa de impresión. **EndPrintPreview** posibilidad de la aplicación para realizar dicha acción. -> PInfo`m_nCurPage` miembro es la página que se mostró por última vez (parte izquierda si se muestran dos páginas) y el puntero es una sugerencia sobre dónde estaba interesado el usuario en la página. Puesto que la estructura de la vista de la aplicación es desconocida para el marco de trabajo, debe proporcionar el código para desplazarse al punto seleccionado.  
  
 Debe realizar la mayoría de las acciones antes de llamar a **CView::EndPrintPreview**. Esta llamada invierte los efectos de **DoPrintPreview** y elimina pView, pDC y pInfo.  
  
```  
// Any further cleanup should be done here.  
CView::EndPrintPreview(pDC,
    pInfo,
    point,
    pView);
```  
  
## <a name="cwinapponfileprintsetup"></a>CWinApp::OnFilePrintSetup  
 Esto se debe asignar para el elemento de menú del programa de instalación de impresión. En la mayoría de los casos, no es necesario reemplazar la implementación.  
  
## <a name="page-nomenclature"></a>Nomenclatura de página  
 Otro problema es el de numeración de las páginas y el orden. Para las aplicaciones de tipo de procesador de textos simple, este es un problema sencillo. La mayoría de los sistemas de vista previa de impresión se supone que cada página impresa se corresponde con una página en el documento.  
  
 Intentar proporcionan una solución generalizada, hay que considerar varios aspectos. Imagine un sistema CAD. El usuario tiene un dibujo que abarca varias hojas de tamaño E. En un tamaño de E (o escalar un menor) trazado, numeración de páginas sería como se muestra en el caso más sencillo. Pero en una impresora láser, imprimir 16 un tamaño de páginas por hoja, lo que tiene la vista preliminar en cuenta una "página"  
  
 Como indica el párrafo de introducción, vista previa de impresión está actuando como una impresora. Por lo tanto, el usuario verá lo que haría derivados de la impresora determinada que está seleccionada. Depende de la vista para determinar qué se imprimirá en cada página.  
  
 La cadena de descripción de la página en el `CPrintInfo` estructura proporciona un medio para mostrar el número de página al usuario si se puede representar como un número por página (como en "Página 1" o "páginas 1-2"). Esta cadena se utiliza la implementación predeterminada de **CPreviewView::OnDisplayPageNumber**. Si se necesita otra pantalla, uno puede invalidar esta función virtual para proporcionar, por ejemplo, "Sheet1, secciones A, B".  
  
## <a name="see-also"></a>Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)

