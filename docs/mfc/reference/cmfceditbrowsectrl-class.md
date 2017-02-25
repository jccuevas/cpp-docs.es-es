---
title: "CMFCEditBrowseCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCEditBrowseCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCEditBrowseCtrl class"
  - "CMFCEditBrowseCtrl constructor"
  - "CMFCEditBrowseCtrl::PreTranslateMessage method"
ms.assetid: 69cfd886-3d35-4bee-8901-7c88fcf9520f
caps.latest.revision: 33
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 35
---
# CMFCEditBrowseCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase de `CMFCEditBrowseCtrl` admite el control de examen de edición, que es un cuadro de texto modificable que contiene opcionalmente un botón examinar.  Cuando el usuario hace clic en el botón examinar, el control realiza una acción personalizada o muestra un cuadro de diálogo estándar que contiene un explorador de archivos o un explorador en la carpeta.  
  
## Sintaxis  
  
```  
class CMFCEditBrowseCtrl : public CEdit  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CMFCEditBrowseCtrl::CMFCEditBrowseCtrl`|Constructor predeterminado.|  
|`CMFCEditBrowseCtrl::~CMFCEditBrowseCtrl`|Un destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCEditBrowseCtrl::EnableBrowseButton](../Topic/CMFCEditBrowseCtrl::EnableBrowseButton.md)|Habilita o deshabilita \(oculta\) el botón examinar.|  
|[CMFCEditBrowseCtrl::EnableFileBrowseButton](../Topic/CMFCEditBrowseCtrl::EnableFileBrowseButton.md)|Habilita el botón examinar y coloca el control de examen de edición en *el modo de exploración del archivo* .|  
|[CMFCEditBrowseCtrl::EnableFolderBrowseButton](../Topic/CMFCEditBrowseCtrl::EnableFolderBrowseButton.md)|Habilita el botón examinar y coloca el control de examen de edición en *el modo de exploración de la carpeta* .|  
|[CMFCEditBrowseCtrl::GetMode](../Topic/CMFCEditBrowseCtrl::GetMode.md)|Devuelve el modo de exploración actual.|  
|[CMFCEditBrowseCtrl::OnAfterUpdate](../Topic/CMFCEditBrowseCtrl::OnAfterUpdate.md)|Llamado por el marco después de que el control de examen de edición se actualice con el resultado de una acción de exploración.|  
|[CMFCEditBrowseCtrl::OnBrowse](../Topic/CMFCEditBrowseCtrl::OnBrowse.md)|Llamado por el marco después de que el usuario haga clic en el botón examinar.|  
|[CMFCEditBrowseCtrl::OnChangeLayout](../Topic/CMFCEditBrowseCtrl::OnChangeLayout.md)|Dibuja de nuevo el control actual de examen de edición.|  
|[CMFCEditBrowseCtrl::OnDrawBrowseButton](../Topic/CMFCEditBrowseCtrl::OnDrawBrowseButton.md)|Llamado por el marco para dibujar el botón examinar.|  
|[CMFCEditBrowseCtrl::OnIllegalFileName](../Topic/CMFCEditBrowseCtrl::OnIllegalFileName.md)|Llamado por el marco cuando un nombre de archivo no válido se escribió en el control de edición.|  
|`CMFCEditBrowseCtrl::PreTranslateMessage`|Traduce mensajes de ventana antes de que se envíen a las funciones de [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) y de [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows.  Para la sintaxis y más información, vea [CWnd::PreTranslateMessage](../Topic/CWnd::PreTranslateMessage.md).|  
|[CMFCEditBrowseCtrl::SetBrowseButtonImage](../Topic/CMFCEditBrowseCtrl::SetBrowseButtonImage.md)|Establece una imagen personalizada para el botón examinar.|  
  
## Comentarios  
 Utilice un control de examen de edición para seleccionar un archivo o la carpeta.  Opcionalmente, utilice el control para realizar una acción personalizada como para mostrar un cuadro de diálogo.  Puede mostrar o no mostrar el botón examinar, y se puede aplicar una etiqueta o una imagen personalizada en el botón.  
  
 *El modo de exploración* del control de examen de edición determina si muestra un botón examinar y qué acción se produce cuando se hace clic en el botón.  Para obtener más información, vea el método de [GetMode](../Topic/CMFCEditBrowseCtrl::GetMode.md) .  
  
 La clase de `CMFCEditBrowseCtrl` admite los modos siguientes.  
  
 `custom mode`  
 Se realiza una acción personalizada cuando el usuario hace clic en el botón examinar.  Por ejemplo, puede mostrar un cuadro de diálogo específico de la aplicación.  
  
 `file mode`  
 Se muestra un cuadro de diálogo estándar de selección de archivos cuando el usuario hace clic en el botón examinar.  
  
 `folder mode`  
 Se muestra un cuadro de diálogo estándar de selección de la carpeta cuando el usuario hace clic en el botón examinar.  
  
## práctico: Especifique una Control de examen de edición  
 Siga estos pasos para proteger un control de examen de edición en la aplicación:  
  
1.  Si desea implementar un modo de exploración personalizado, derive poseen la clase de la clase de `CMFCEditBrowseCtrl` y después reemplazan el método de [CMFCEditBrowseCtrl::OnBrowse](../Topic/CMFCEditBrowseCtrl::OnBrowse.md) .  En el método invalidado, ejecute una acción personalizada de examen y actualiza el control de examen de edición con el resultado.  
  
2.  Inserte el objeto de `CMFCEditBrowseCtrl` o el objeto derivado de control de examen de edición en el objeto de la ventana primaria.  
  
3.  Si utiliza **Asistente para clases** para crear un cuadro de diálogo, agregue un control de edición \(`CEdit`\) al formulario de cuadro de diálogo.  Además, agregue una variable para tener acceso al control en el archivo de encabezado.  en el archivo de encabezado, cambie el tipo de la variable de `CEdit` a `CMFCEditBrowseCtrl`.  El control de examen de edición se creará automáticamente.  Si no utiliza **Asistente para clases**, agregue una variable de `CMFCEditBrowseCtrl` al archivo de encabezado y llame al método de `Create` .  
  
4.  Si agrega un control de examen de edición a un cuadro de diálogo, utilice la herramienta de **ClassWizard** para configurar intercambio de datos.  
  
5.  Llame al método de [EnableFolderBrowseButton](../Topic/CMFCEditBrowseCtrl::EnableFolderBrowseButton.md), de [EnableFileBrowseButton](../Topic/CMFCEditBrowseCtrl::EnableFileBrowseButton.md), o de [EnableBrowseButton](../Topic/CMFCEditBrowseCtrl::EnableBrowseButton.md) para establecer el modo de exploración y mostrar el botón examinar.  Llame al método de [GetMode](../Topic/CMFCEditBrowseCtrl::GetMode.md) para obtener el modo de exploración actual.  
  
6.  Para proporcionar una imagen personalizada para el botón examinar, llame al método de [SetBrowseButtonImage](../Topic/CMFCEditBrowseCtrl::SetBrowseButtonImage.md) o invalide el método de [OnDrawBrowseButton](../Topic/CMFCEditBrowseCtrl::OnDrawBrowseButton.md) .  
  
7.  Para quitar el botón examinar del control de examen de edición, llame al método de [EnableBrowseButton](../Topic/CMFCEditBrowseCtrl::EnableBrowseButton.md) con el parámetro de `bEnable` establecido en `FALSE`.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CEdit](../../mfc/reference/cedit-class.md)  
  
 [CMFCEditBrowseCtrl](../../mfc/reference/cmfceditbrowsectrl-class.md)  
  
## Ejemplo  
 El ejemplo siguiente se muestra cómo utilizar dos métodos en la clase de `CMFCEditBrowseCtrl` : `EnableFolderBrowseButton` y `EnableFileBrowseButton`.  Este ejemplo forma parte de [nuevo ejemplo de Controles](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#6](../../mfc/reference/codesnippet/CPP/cmfceditbrowsectrl-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#7](../../mfc/reference/codesnippet/CPP/cmfceditbrowsectrl-class_2.cpp)]  
  
## Requisitos  
 **encabezado:** afxeditbrowsectrl.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)