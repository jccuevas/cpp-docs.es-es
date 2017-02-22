---
title: "CFontDialog Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CFontDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CFontDialog class"
  - "cuadros de diálogo, fuentes"
  - "fuentes"
  - "fuentes, seleccionar"
ms.assetid: 6228d500-ed0f-4156-81e5-ab0d57d1dcf4
caps.latest.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 27
---
# CFontDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Permite incorporar un cuadro de diálogo de selección de fuente en su aplicación.  
  
## Sintaxis  
  
```  
class CFontDialog : public CCommonDialog  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFontDialog::CFontDialog](../Topic/CFontDialog::CFontDialog.md)|Crea un objeto `CFontDialog`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFontDialog::DoModal](../Topic/CFontDialog::DoModal.md)|Muestra el cuadro de diálogo y permite que el usuario realice una selección.|  
|[CFontDialog::GetCharFormat](../Topic/CFontDialog::GetCharFormat.md)|Recupera el formato de caracteres de la fuente seleccionada.|  
|[CFontDialog::GetColor](../Topic/CFontDialog::GetColor.md)|Devuelve el color de la fuente seleccionada.|  
|[CFontDialog::GetCurrentFont](../Topic/CFontDialog::GetCurrentFont.md)|Asigna las características de la fuente seleccionada a una estructura de `LOGFONT` .|  
|[CFontDialog::GetFaceName](../Topic/CFontDialog::GetFaceName.md)|Devuelve el nombre de fuente de la fuente seleccionada.|  
|[CFontDialog::GetSize](../Topic/CFontDialog::GetSize.md)|Devuelve el tamaño en puntos de la fuente seleccionada.|  
|[CFontDialog::GetStyleName](../Topic/CFontDialog::GetStyleName.md)|Devuelve el nombre del estilo de la fuente seleccionada.|  
|[CFontDialog::GetWeight](../Topic/CFontDialog::GetWeight.md)|Devuelve la proporción de la fuente seleccionada.|  
|[CFontDialog::IsBold](../Topic/CFontDialog::IsBold.md)|Determina si la fuente está en negrita.|  
|[CFontDialog::IsItalic](../Topic/CFontDialog::IsItalic.md)|Determina si la fuente está en cursiva.|  
|[CFontDialog::IsStrikeOut](../Topic/CFontDialog::IsStrikeOut.md)|Determina si se muestra la fuente con tachado.|  
|[CFontDialog::IsUnderline](../Topic/CFontDialog::IsUnderline.md)|Determina si subrayan a la fuente.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFontDialog::m\_cf](../Topic/CFontDialog::m_cf.md)|Una estructura utilizada para personalizar un objeto de `CFontDialog` .|  
  
## Comentarios  
 Un objeto de `CFontDialog` es un cuadro de diálogo con una lista de fuentes que se hayan instalado actualmente en el sistema.  El usuario puede seleccionar una fuente concreta de la lista, y esta selección se notifica a la aplicación.  
  
 Para construir un objeto de `CFontDialog` , utilizar el constructor suministrado o derivar una nueva subclase y utilizar su propio constructor personalizado.  
  
 Una vez que se ha construido un objeto de `CFontDialog` , puede utilizar la estructura de `m_cf` para inicializar los valores o estados de controles en el cuadro de diálogo.  La estructura de [m\_cf](../Topic/CFontDialog::m_cf.md) es de [CHOOSEFONT](http://msdn.microsoft.com/library/windows/desktop/ms646832)escrito.  Para obtener más información sobre esta estructura, vea [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Después de inicializar los controles del diálogo, llame a la función miembro de `DoModal` para mostrar el cuadro de diálogo y para permitir que el usuario seleccione una fuente.  `DoModal` devuelve si el usuario ha seleccionado del botón ACEPTAR \(**IDOK**\) o delete \(**IDCANCEL**\).  
  
 Si `DoModal` devuelve **IDOK**, puede utilizar una de las funciones miembro de entity\_CODECFontDialog para recuperar la entrada de información del usuario.  
  
 Puede utilizar la función de Windows [CommDlgExtendedError](http://msdn.microsoft.com/library/windows/desktop/ms646916) para determinar si se ha producido un error durante la inicialización del cuadro de diálogo y para obtener más información sobre el error.  Para obtener más información sobre esta función, vea [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 `CFontDialog` se basa en el archivo de COMMDLG.DLL que envía con las versiones de Windows 3,1 y versiones posteriores.  
  
 Para personalizar el cuadro de diálogo, derive una clase de `CFontDialog`, proporcione una plantilla personalizada del cuadro de diálogo, y agregue un mensaje\- mapa para procesar mensajes de notificación de controles extendidos.  cualquier mensaje sin procesar se debe pasar a la clase base.  
  
 Personalizar la función de enlace no es necesario.  
  
 Para obtener más información sobre cómo utilizar `CFontDialog`, vea [Clases comunes de diálogo](../../mfc/common-dialog-classes.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 `CFontDialog`  
  
## Requisitos  
 **encabezado:** afxdlgs.h  
  
## Vea también  
 [ejemplo HIERSVR de MFC](../../top/visual-cpp-samples.md)   
 [CCommonDialog Class](../../mfc/reference/ccommondialog-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)