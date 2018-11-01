---
title: 'TN030: Personalizar la impresión y la vista previa de impresión'
ms.date: 06/28/2018
f1_keywords:
- vc.print
helpviewer_keywords:
- TN030
- customizing printing and print preview
- printing [MFC], views
- printing views [MFC]
- print preview [MFC], customizing
ms.assetid: 32744697-c91c-41b6-9a12-b8ec01e0d438
ms.openlocfilehash: 09938c5cec2812998d5e76e15154754ad3ac3e0b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50667914"
---
# <a name="tn030-customizing-printing-and-print-preview"></a>TN030: Personalizar la impresión y la vista previa de impresión

> [!NOTE]
> La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea. Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos. Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.

Esta nota se describe el proceso de personalización de impresión y vista previa y describe los propósitos de las rutinas de devolución de llamada que usa en `CView` y las rutinas de devolución de llamada y las funciones miembro de `CPreviewView`.

## <a name="the-problem"></a>El problema

MFC proporciona una solución completa para la mayoría de impresión y vista previa de impresión debe. En la mayoría de los casos, es necesario tener una vista puede imprimir y obtener una vista previa poco de código adicional. Sin embargo, hay formas de optimizar la impresión que requieren un esfuerzo considerable por parte del desarrollador, y algunas aplicaciones necesitan agregar elementos de la interfaz de usuario específico para el modo de vista previa de impresión.

## <a name="efficient-printing"></a>Impresión eficaz

Cuando una aplicación MFC imprime utilizando los métodos estándares, Windows dirige todas las llamadas de salida de la interfaz de dispositivo gráfico (GDI) a un metarchivo en memoria. Cuando `EndPage` es llamado, Windows reproduce el metarchivo una vez para cada banda físico que requiere la impresora para imprimir una página. Durante este procesamiento, GDI realiza consultas frecuentes sobre el procedimiento Abort para determinar si debería continuar. Normalmente, el procedimiento de anulación permite mensajes que deben procesarse para que el usuario puede cancelar el trabajo de impresión mediante un cuadro de diálogo de impresión.

Lamentablemente, esto puede ralentizar el proceso de impresión. Si la impresión en la aplicación debe ser más rápida que puede lograrse mediante la técnica estándar, debe implementar las bandas manual.

## <a name="print-banding"></a>Imprimir las bandas

Con el fin de la banda manualmente, debe volver implementar el bucle de impresión que `OnPrint` se llama varias veces por página (una vez por banda). El bucle de impresión se implementa en el `OnFilePrint` función en viewprnt.cpp. En su `CView`-clase derivada, esta función se sobrecarga para que la entrada de asignación de mensaje para controlar el comando de impresión llama a la función de impresión. Copia el `OnFilePrint` rutina y cambie el bucle de impresión para implementar las bandas. Probablemente también desea pasar el rectángulo bandas para las funciones de impresión para que se puede optimizar el dibujo basado en la sección de la página que se está imprimiendo.

En segundo lugar, debe llamar con frecuencia `QueryAbort` al dibujar la banda. En caso contrario, no se llamará al procedimiento anular y el usuario podrá cancelar el trabajo de impresión.

## <a name="print-preview-electronic-paper-with-user-interface"></a>Vista previa de impresión: Papel electrónico con la interfaz de usuario

Vista preliminar, en esencia, intenta activar la presentación en una emulación de una impresora. De forma predeterminada, el área de cliente de la ventana principal se usa para mostrar una o dos páginas completamente dentro de la ventana. El usuario es capaz de acercar un área de la página para verlo con más detalle. Con compatibilidad adicional, el usuario puede incluso podrá editar el documento en modo de vista previa.

## <a name="customizing-print-preview"></a>Personalizar la vista previa de impresión

Esta nota solo se ocupa uno de los aspectos de la modificación de la vista previa de impresión: adición de interfaz de usuario para el modo de vista previa. Son posibles otras modificaciones, pero estos cambios están fuera del ámbito de esta discusión.

## <a name="to-add-ui-to-the-preview-mode"></a>Para agregar la interfaz de usuario para el modo de vista previa

1. Derive una clase de vista de `CPreviewView`.

2. Agregar controladores de comandos para los aspectos de la interfaz de usuario que desee.

3. Si va a agregar los aspectos visuales a la presentación, invalidar `OnDraw` y llevar a cabo el dibujo después de llamar a `CPreviewView::OnDraw`.

## <a name="onfileprintpreview"></a>OnFilePrintPreview

Este es el controlador de comandos para la vista previa de impresión. La implementación predeterminada es:

```cpp
void CView::OnFilePrintPreview()
{
    // In derived classes, implement special window handling here
    // Be sure to Unhook Frame Window close if hooked.

    // must not create this on the frame. Must outlive this function
    CPrintPreviewState* pState = new CPrintPreviewState;

    if (!DoPrintPreview(AFX_IDD_PREVIEW_TOOLBAR, this,
        RUNTIME_CLASS(CPreviewView), pState))
    {
        // In derived classes, reverse special window handling
        // here for Preview failure case

        TRACE0("Error: DoPrintPreview failed");
        AfxMessageBox(AFX_IDP_COMMAND_FAILURE);
        delete pState;  // preview failed to initialize, delete State now
    }
}
```

`DoPrintPreview` oculta el panel principal de la aplicación. Barras de control, como la barra de estado, se pueden conservar especificándolos en el pState ->*dwStates* miembro (que es una máscara de bits y los bits para barras de control individuales se definen por AFX_CONTROLBAR_MASK (AFX_IDW_MYBAR)). La ventana pState ->*nIDMainPane* es la ventana que se oculta automáticamente y reshown. `DoPrintPreview` a continuación, creará una barra de botones de la interfaz de usuario de vista previa estándar. Si se necesita control de ventana especial, por ejemplo, para ocultar o mostrar otras ventanas, que deben realizarse antes de `DoPrintPreview` se llama.

De forma predeterminada, cuando finaliza la vista previa de impresión, devuelve las barras de control a su estado original y el panel principal a visible. Si se necesita un tratamiento especial, debe realizarse en un reemplazo de `EndPrintPreview`. Si `DoPrintPreview` se produce un error, también proporcionan un control especial.

Se llama a DoPrintPreview con:

- El identificador de recurso de la plantilla de cuadro de diálogo para la barra de herramientas de vista previa.

- Un puntero a la vista para realizar la impresión de la vista previa de impresión.

- La clase de tiempo de ejecución de la clase de vista previa. Esto se creará dinámicamente en DoPrintPreview.

- El puntero CPrintPreviewState. Tenga en cuenta que la estructura CPrintPreviewState (o la estructura derivada si la aplicación necesita más estado mantenido) debe *no* crearse en el marco. DoPrintPreview es no modal y debe sobrevivir a esta estructura hasta que se llama EndPrintPreview.

  > [!NOTE]
  > Si se necesita una vista independiente o una clase de vista de compatibilidad con la impresión, se debe pasar un puntero a ese objeto como segundo parámetro.

## <a name="endprintpreview"></a>EndPrintPreview

Esto se llama para finalizar el modo de vista previa de impresión. Suele ser deseable para pasar a la página en el documento que se mostró por última vez en vista previa de impresión. `EndPrintPreview` es la oportunidad de la aplicación para hacer eso. -> PInfo*m_nCurPage* miembro es la página que se mostró por última vez (la parte izquierda si se muestran dos páginas) y el puntero es una sugerencia sobre dónde estaba interesado el usuario en la página. Puesto que la estructura de la vista de la aplicación es desconocida para el marco de trabajo, a continuación, debe proporcionar el código para desplazarse al punto seleccionado.

Debe realizar la mayoría de las acciones antes de llamar a `CView::EndPrintPreview`. Esta llamada invierte los efectos de `DoPrintPreview` y elimina pView, pDC y pInfo.

```cpp
// Any further cleanup should be done here.
CView::EndPrintPreview(pDC, pInfo, point, pView);
```

## <a name="cwinapponfileprintsetup"></a>CWinApp::OnFilePrintSetup

Esto se debe asignar para el elemento de menú de instalación de impresión. En la mayoría de los casos, no es necesario que invalide la implementación.

## <a name="page-nomenclature"></a>Nomenclatura de página

Otro problema es de numeración de páginas y el orden. Para las aplicaciones de tipo de procesador de textos sencillo, este es un problema sencillo. La mayoría de los sistemas de vista previa de impresión se suponen que cada página impresa se corresponde con una página en el documento.

Al intentar ofrecer una solución generalizada, hay que considerar varios aspectos. Imagine un sistema de CAD. El usuario tiene un dibujo que abarca varias hojas de tamaño E. En un tamaño E (o escala más pequeña y) plotter, numeración de páginas sería como se muestra en el caso más sencillo. Pero en una impresora láser, impresión 16 un tamaño de páginas por hoja, lo que tiene la vista preliminar en cuenta una "página"

Como indica el párrafo de introducción, vista previa de impresión está actuando como una impresora. Por lo tanto, el usuario verá lo que vendría fuera de la impresora determinada que está seleccionada. Es la vista para determinar qué imagen se imprime en cada página.

La cadena de descripción de página en el `CPrintInfo` estructura proporciona un medio para mostrar el número de página al usuario si se puede representar como un número por página (como en "Página 1" o "páginas 1-2"). Esta cadena se usa la implementación predeterminada de `CPreviewView::OnDisplayPageNumber`. Si se necesita otra pantalla, uno puede invalidar esta función virtual para proporcionar, por ejemplo, "Hoja1, secciones A, B".

## <a name="see-also"></a>Vea también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)
