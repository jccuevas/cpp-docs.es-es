---
title: "CEditView Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CEditView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CEditView class"
  - "edit controls, clases"
  - "text editors"
  - "text editors, CEditView class"
  - "vistas, clases"
ms.assetid: bf38255c-fcbe-450c-95b2-3c5e35f86c37
caps.latest.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 27
---
# CEditView Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Un tipo de clase de vista que proporciona la funcionalidad de un control de edición de Windows y se puede utilizar para implementar funcionalidad simple del editor de texto.  
  
## Sintaxis  
  
```  
class CEditView : public CCtrlView  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CEditView::CEditView](../Topic/CEditView::CEditView.md)|construye un objeto de `CEditView`escrito.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CEditView::FindText](../Topic/CEditView::FindText.md)|Buscar una cadena dentro del texto.|  
|[CEditView::GetBufferLength](../Topic/CEditView::GetBufferLength.md)|Obtiene la longitud del búfer del carácter.|  
|[CEditView::GetEditCtrl](../Topic/CEditView::GetEditCtrl.md)|Proporciona acceso a la parte de `CEdit` de un objeto de `CEditView` \(control de edición de Windows\).|  
|[CEditView::GetPrinterFont](../Topic/CEditView::GetPrinterFont.md)|Recuperar la fuente de la actual.|  
|[CEditView::GetSelectedText](../Topic/CEditView::GetSelectedText.md)|Recupera la selección actual del texto.|  
|[CEditView::LockBuffer](../Topic/CEditView::LockBuffer.md)|bloquea el búfer.|  
|[CEditView::PrintInsideRect](../Topic/CEditView::PrintInsideRect.md)|Genera el interior de texto un rectángulo determinado.|  
|[CEditView::SerializeRaw](../Topic/CEditView::SerializeRaw.md)|Serializa un objeto de `CEditView` en el disco como texto sin formato.|  
|[CEditView::SetPrinterFont](../Topic/CEditView::SetPrinterFont.md)|Establece una nueva fuente de impresora.|  
|[CEditView::SetTabStops](../Topic/CEditView::SetTabStops.md)|Establecen tabulaciones para la presentación en pantalla y la impresión.|  
|[CEditView::UnlockBuffer](../Topic/CEditView::UnlockBuffer.md)|desbloquea el búfer.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CEditView::OnFindNext](../Topic/CEditView::OnFindNext.md)|Encuentra la siguiente aparición de una cadena de texto.|  
|[CEditView::OnReplaceAll](../Topic/CEditView::OnReplaceAll.md)|Reemplaza todas las apariciones de una cadena especificada por una cadena nueva.|  
|[CEditView::OnReplaceSel](../Topic/CEditView::OnReplaceSel.md)|reemplaza la selección actual.|  
|[CEditView::OnTextNotFound](../Topic/CEditView::OnTextNotFound.md)|Llamado cuando una operación de búsqueda no puede para coincidir aún más texto.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CEditView::dwStyleDefault](../Topic/CEditView::dwStyleDefault.md)|Estilo predeterminado de los objetos de **CEditView.**tipo|  
  
## Comentarios  
 La clase de `CEditView` proporciona funciones adicionales siguientes:  
  
-   Imprimir.  
  
-   Buscar y reemplazar.  
  
 Dado que la clase `CEditView` es un derivado de la clase `CView`, los objetos de la clase `CEditView` se pueden utilizar con documentos y plantillas de documento.  
  
 El texto de cada control de `CEditView` se mantiene su propio objeto de memoria.  la aplicación puede tener cualquier número de objetos de `CEditView` .  
  
 Crear los objetos de `CEditView` tipo si desea que una ventana de edición con la funcionalidad agregada citada anteriormente, o si desea funcionalidad simple del editor de texto.  un objeto de `CEditView` puede ocupar el área cliente completa de una ventana.  Derive poseen clases de `CEditView` para agregar o modificar la funcionalidad básica, o para declarar las clases que se pueden agregar a una plantilla de documento.  
  
 La implementación predeterminada de la clase `CEditView` controla los comandos siguientes: **ID\_EDIT\_SELECT\_ALL**, **ID\_EDIT\_FIND**, **ID\_EDIT\_REPLACE**, **ID\_EDIT\_REPEAT**, y **ID\_FILE\_PRINT**.  
  
 El límite predeterminado de caracteres para `CEditView` es \(1024 \* 1024 \- 1 \= 1048575\).  Esto se puede modificar llamando a la función de **EM\_LIMITTEXT** del control de edición subyacente.  Sin embargo, los límites varían en función del sistema operativo y el tipo de control edit \(único o multilínea\).  Para obtener más información sobre estos límites, vea [EM\_LIMITTEXT](http://msdn.microsoft.com/library/windows/desktop/bb761607).  
  
 Para cambiar este límite en el control, invalide la función de `OnCreate()` para la clase de `CEditView` y escriba la siguiente línea de código:  
  
 [!code-cpp[NVC_MFCDocView#65](../../mfc/codesnippet/CPP/ceditview-class_1.cpp)]  
  
 Los objetos de `CEditView` tipo \(o de los tipos derivados de `CEditView`\) tienen las siguientes limitaciones:  
  
-   `CEditView` no implementa true lo que se ve es lo que se obtiene \(WYSIWYG\) la edición.  Donde existe una opción entre la legibilidad de la presentación y el resultado de impresión coincidente, `CEditView` opta por legibilidad de la pantalla.  
  
-   `CEditView` puede mostrar texto en una sola fuente.  No se admite ningún formato de carácter especial.  Vea la clase [CRichEditView](../../mfc/reference/cricheditview-class.md) por mayores capacidades.  
  
-   La cantidad de texto que `CEditView` puede contener es limitada.  Los límites son iguales que para el control de `CEdit` .  
  
 Para obtener más información sobre `CEditView`, vea [Clases derivadas de vista disponible en MFC](../../mfc/derived-view-classes-available-in-mfc.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CCtrlView](../../mfc/reference/cctrlview-class.md)  
  
 `CEditView`  
  
## Requisitos  
 **encabezado:** afxext.h  
  
## Vea también  
 [ejemplo SUPERPAD de MFC](../../top/visual-cpp-samples.md)   
 [CCtrlView Class](../../mfc/reference/cctrlview-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CEdit Class](../../mfc/reference/cedit-class.md)   
 [CDocument Class](../../mfc/reference/cdocument-class.md)   
 [CDocTemplate Class](../../mfc/reference/cdoctemplate-class.md)   
 [CCtrlView Class](../../mfc/reference/cctrlview-class.md)   
 [CRichEditView Class](../../mfc/reference/cricheditview-class.md)