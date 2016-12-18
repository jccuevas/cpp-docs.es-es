---
title: "TN030: Personalizar la impresi&#243;n y la vista previa de impresi&#243;n | Microsoft Docs"
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
  - "vc.print"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "personalizar la impresión y la vista previa de impresión"
  - "vista previa de impresión, personalizar"
  - "imprimir [MFC], vistas"
  - "imprimir vistas"
  - "TN030"
ms.assetid: 32744697-c91c-41b6-9a12-b8ec01e0d438
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN030: Personalizar la impresi&#243;n y la vista previa de impresi&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea.  Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos.  Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.  
  
 Esta nota describe el proceso de personalización de impresión y vista previa de impresión y describe los efectos de las rutinas de devolución de llamada utilizadas en `CView` y las rutinas de devolución de llamada y las funciones miembro de **CPreviewView**.  
  
## El problema  
 MFC proporciona una solución completa para la mayoría de impresión y vista previa de impresión.  En la mayoría de los casos, no será necesario código adicional para tener una vista capaz de imprimir y obtener una vista previa.  Sin embargo, existen las maneras de optimizar la impresión que requieren esfuerzo significativo del desarrollador, y algunas aplicaciones necesitan agregar elementos específicos de la interfaz de usuario en el modo vista previa de impresión.  
  
## Impresión eficaz  
 Cuando una aplicación MFC imprime utilizando los métodos estándar, Windows dirige todas las llamadas gráficas de salida de \(GDI\) de la interfaz de dispositivo a un metarchivo de en\- memoria.  Cuando se llama a `EndPage` , Windows reproduce el metarchivo una vez para cada banda física que la impresora requiere para imprimir una página.  Durante esta representación, GDI consultas con frecuencia el procedimiento abort para determinar si continúa.  El procedimiento abort suele permitir que los mensajes son procesados de modo que el usuario puede anular el trabajo de impresión mediante un cuadro de diálogo de impresión.  
  
 Desgraciadamente, esto puede reducir el proceso de impresión.  Si la impresión de la aplicación debe ser más rápida que puede tener acceso mediante la técnica estándar, debe implementar las bandas manuales.  
  
## Bandas de impresión  
 Para manualmente banda, debe con referencia al implementar el bucle de impresión tales que `OnPrint` se llama varias veces por página \(una vez por banda\).  El bucle de impresión se implementa en función de **OnFilePrint** en viewprnt.cpp.  En `CView`\- clase derivada, se sobrecarga esta función para que la entrada del mapa de mensajes para administrar el comando de impresión llame a la función de impresión.  Copie la rutina de **OnFilePrint** y cambie el bucle de impresión para implementar las bandas.  Probablemente también deseará pasar el rectángulo de las bandas a las funciones de impresión para poder optimizar el gráfico basado en la sección de la página que está impresa.  
  
 En segundo lugar, debe con frecuencia llamar `QueryAbort` mientras dibuja la banda.  Si no, el procedimiento abort no se denominará y el usuario no podrá cancelar el trabajo de impresión.  
  
## Vista previa de impresión: Paper electrónico con la interfaz de usuario  
 La vista previa de impresión, esencialmente, intenta activar la presentación en una emulación de una impresora.  De forma predeterminada, el área de cliente de la ventana principal se utiliza para mostrar una o dos páginas totalmente dentro de la ventana.  El usuario puede para ampliar un área de la página verlo con más detalle.  Con compatibilidad adicional, el usuario puede incluso tener la posibilidad de modificar el documento en modo de vista previa.  
  
## Personalizar la vista previa de impresión  
 Esta nota se ocupa solo de un aspecto de vista previa de impresión de modificación: Interfaz de usuario al modo de vista previa.  Otras modificaciones son posibles, pero estos cambios están fuera del ámbito de este tutorial.  
  
## Para agregar interfaz de usuario al modo de vista previa  
  
1.  Derive una clase de vista de **CPreviewView**.  
  
2.  Agregue controladores de comandos para los aspectos de la interfaz de usuario que desee.  
  
3.  Si está agregando los aspectos visuales en la pantalla, el reemplazo `OnDraw` y realiza el gráfico después de llamar a **CPreviewView::OnDraw.**  
  
## OnFilePrintPreview  
 Éste es el controlador de comandos para la vista previa de impresión.  La implementación predeterminada es:  
  
```  
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
        delete pState;      // preview failed to initialize,   
                    // delete State now  
    }  
}  
```  
  
 **DoPrintPreview** ocultará el panel principal de la aplicación.  Las barras de controles, como la barra de estado, pueden conservarse especificándolos en el\>miembro de**dwStates** de pState\- \(Esta es una máscara de bits y los bits para las barras de controles individuales están definidos por **AFX\_CONTROLBAR\_MASK**\(AFX\_IDW\_MYBAR\)\).  El pState\-**nIDMainPane** \>de la ventana es la ventana que automáticamente se oculta y reshown.  **DoPrintPreview** a continuación creará una barra de botones para la interfaz de usuario estándar de vista previa.  Si es especial el control de la ventana es necesario, por ejemplo ocultar o mostrar otras ventanas, que debe hacer antes de que se llame a **DoPrintPreview** .  
  
 De forma predeterminada, cuando la vista previa de impresión finaliza, devuelve las barras de control a sus estados originales y el panel principal a visible.  Si el tratamiento especial es necesario, debe hacer en un reemplazo de **EndPrintPreview.** Si se produce **DoPrintPreview** , también proporciona un tratamiento especial.  
  
 DoPrintPreview lleva:  
  
-   El Id. de recurso de plantilla de cuadro de diálogo para la barra de herramientas de vista previa.  
  
-   Un puntero a la vista para realizar la impresión para la vista previa de impresión.  
  
-   La clase en tiempo de ejecución de la clase de vista de la vista previa.  Se crea dinámicamente en DoPrintPreview.  
  
-   El puntero de CPrintPreviewState.  Observe que la estructura de CPrintPreviewState \(o estructura derivada si la aplicación necesita a más estado conservará\) no se debe crear en el cuadro.  DoPrintPreview es no modal y esta estructura debe sobrevivir hasta que se llame a EndPrintPreview.  
  
    > [!NOTE]
    >  Si una vista o una clase independiente de la vista es necesaria para imprimir el soporte, un puntero a dicho objeto se debe pasar como segundo parámetro.  
  
## EndPrintPreview  
 Esto se denomina finalizar el modo de vista previa de impresión.  Se aconseja desplazarse a la página del documento generado por último en vista previa de impresión.  **EndPrintPreview** es la oportunidad de la aplicación de ello.  El miembro\>de`m_nCurPage` de pInfo\- es la página que mostrada por última vez \(de izquierda si dos páginas se muestran\), y el puntero es una sugerencia con respecto a dónde en la página estaba interesado el usuario.  Puesto que la estructura de la vista de la aplicación se desconoce el marco, debe proporcionar código para desplazarse a punto elegido.  
  
 Debe realizar la mayoría de acciones antes de llamar a **CView::EndPrintPreview**.  Esta llamada invierte los efectos de **DoPrintPreview** y elimina el pView, el pDC, y el pInfo.  
  
```  
// Any further cleanup should be done here.  
CView::EndPrintPreview(pDC, pInfo, point, pView);  
```  
  
## CWinApp::OnFilePrintSetup  
 Esto se debe asignar para el elemento de menú de configuración de impresión.  En la mayoría de los casos, no es necesario reemplazar la implementación.  
  
## Nomenclatura de la página  
 El otro tema es el de numeración y pedido de página.  Para las aplicaciones sencillas del tipo de procesador de textos, es un problema directo.  La mayoría de los sistemas de vista previa de impresión se supone que cada página impresa corresponde a una página del documento.  
  
 En intentar proporcionar una solución generalizada, debe tener en cuenta varios aspectos.  Imagine un sistema de CAD.  El usuario tiene un gráfico que cubre varias hojas de E\- tamaño.  En un trazador gráfico de E\- tamaño \(o un menor, escalado\), la numeración de página sería como en el caso sencillo.  ¿Pero en una impresora láser, imprimir 16 páginas de Uno\- tamaño por la hoja, la vista previa de impresión considera una “página”?  
  
 Como los estados introductorias de párrafo, vista previa de impresión está actuando como una impresora.  Por consiguiente, el usuario verá qué saldría printer determinada está seleccionado.  Depende de la vista para determinar qué imagen se imprime en cada página.  
  
 La cadena de descripción de la página en la estructura de `CPrintInfo` proporciona un medio para mostrar el número de página al usuario si puede representarse como un número por página \(como en la página 1 " o “páginas 1\-2”\). Esta cadena utiliza la implementación predeterminada de **CPreviewView::OnDisplayPageNumber**.  Si otra pantalla es necesaria, se puede invalidar esta función virtual para proporcionar, por ejemplo, “Sheet1, secciones A, b”.  
  
## Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)