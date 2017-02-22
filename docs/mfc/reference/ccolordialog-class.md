---
title: "CColorDialog Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CColorDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CColorDialog class"
  - "colores, cuadro de diálogo"
  - "cuadros de diálogo, colores"
ms.assetid: d013dc25-9290-4b5d-a97e-95ad7208e13b
caps.latest.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# CColorDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Permite incorporar un cuadro de diálogo de la color\-selección en la aplicación.  
  
## Sintaxis  
  
```  
class CColorDialog : public CCommonDialog  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CColorDialog::CColorDialog](../Topic/CColorDialog::CColorDialog.md)|Crea un objeto `CColorDialog`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CColorDialog::DoModal](../Topic/CColorDialog::DoModal.md)|Muestra un cuadro de diálogo color y permite que el usuario realice una selección.|  
|[CColorDialog::GetColor](../Topic/CColorDialog::GetColor.md)|devuelve una estructura de **COLORREF** que contiene los valores de color seleccionado.|  
|[CColorDialog::GetSavedCustomColors](../Topic/CColorDialog::GetSavedCustomColors.md)|recupera los colores personalizados creados por el usuario.|  
|[CColorDialog::SetCurrentColor](../Topic/CColorDialog::SetCurrentColor.md)|Fuerza la selección de color actual al color especificado.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CColorDialog::OnColorOK](../Topic/CColorDialog::OnColorOK.md)|Reemplace para validar color escrito en el cuadro de diálogo.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CColorDialog::m\_cc](../Topic/CColorDialog::m_cc.md)|Una estructura utilizada para personalizar los valores del cuadro de diálogo.|  
  
## Comentarios  
 Un objeto de `CColorDialog` es un cuadro de diálogo con una lista de colores que se definen para el sistema de visualización.  El usuario puede seleccionar o crear un color determinado de la lista, que a continuación se muestra de nuevo a la aplicación al salir del cuadro de diálogo.  
  
 Para construir un objeto de `CColorDialog` , utilizar el constructor suministrado o derivar una nueva clase y utilizarla para formar el constructor personalizado.  
  
 Una vez que se ha construido el cuadro de diálogo, puede establecer o modificar cualquier valor de la estructura de[m\_cc](../Topic/CColorDialog::m_cc.md) para inicializar los valores de los controles del cuadro de diálogo.  La estructura de `m_cc` es de [CHOOSECOLOR](http://msdn.microsoft.com/library/windows/desktop/ms646830)escrito.  
  
 Después de inicializar los controles del cuadro de diálogo, llame a la función miembro de `DoModal` para mostrar el cuadro de diálogo y para permitir que el usuario seleccione un color.  `DoModal` devuelve la selección del usuario de botón de OK \(**IDOK**\) o eliminación del cuadro de diálogo \(**IDCANCEL**\).  
  
 Si `DoModal` devuelve **IDOK**, puede utilizar una de las funciones miembro de los entity\_CColorDialog para recuperar la entrada de información del usuario.  
  
 Puede utilizar la función de Windows [CommDlgExtendedError](http://msdn.microsoft.com/library/windows/desktop/ms646916) para determinar si se ha producido un error durante la inicialización del cuadro de diálogo y para obtener más información sobre el error.  
  
 `CColorDialog` se basa en el archivo de COMMDLG.DLL que envía con las versiones de Windows 3,1 y versiones posteriores.  
  
 Para personalizar el cuadro de diálogo, derive una clase de `CColorDialog`, proporcionar una plantilla personalizada del cuadro de diálogo, y agregar un mapa de mensajes para procesar mensajes de notificación de controles extendidos.  cualquier mensaje sin procesar se debe pasar a la clase base.  
  
 Personalizar la función de enlace no es necesario.  
  
> [!NOTE]
>  En algunas instalaciones el objeto de `CColorDialog` no se mostrará con un fondo gris si ha utilizado el marco para que atenuadas otros objetos de `CDialog` .  
  
 Para obtener más información sobre cómo utilizar `CColorDialog`, vea [Clases comunes de diálogo](../../mfc/common-dialog-classes.md)  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 `CColorDialog`  
  
## Requisitos  
 **encabezado:** afxdlgs.h  
  
## Vea también  
 [ejemplo MDI de MFC](../../top/visual-cpp-samples.md)   
 [ejemplo DRAWCLI de MFC](../../top/visual-cpp-samples.md)   
 [CCommonDialog Class](../../mfc/reference/ccommondialog-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)