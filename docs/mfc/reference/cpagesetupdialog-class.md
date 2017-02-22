---
title: "CPageSetupDialog Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CPageSetupDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CPageSetupDialog class"
  - "OLE Page Setup dialog box"
  - "configuración de página"
  - "Configurar página (cuadro de diálogo)"
  - "Print Setup dialog box"
ms.assetid: 049c0ac8-f254-4854-9414-7a8271d1447a
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# CPageSetupDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Encapsula los servicios proporcionados por el cuadro de diálogo OLE común de la configuración de página de Windows de compatibilidad adicional para los márgenes de impresión que establecen y modificar.  
  
## Sintaxis  
  
```  
class CPageSetupDialog : public CCommonDialog  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPageSetupDialog::CPageSetupDialog](../Topic/CPageSetupDialog::CPageSetupDialog.md)|Crea un objeto `CPageSetupDialog`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPageSetupDialog::CreatePrinterDC](../Topic/CPageSetupDialog::CreatePrinterDC.md)|Crea un contexto para imprimir.|  
|[CPageSetupDialog::DoModal](../Topic/CPageSetupDialog::DoModal.md)|Muestra el cuadro de diálogo y permite al usuario realizan una selección.|  
|[CPageSetupDialog::GetDeviceName](../Topic/CPageSetupDialog::GetDeviceName.md)|Devuelve el nombre de dispositivo de la impresora.|  
|[CPageSetupDialog::GetDevMode](../Topic/CPageSetupDialog::GetDevMode.md)|Devuelve `DEVMODE` actual de la impresora.|  
|[CPageSetupDialog::GetDriverName](../Topic/CPageSetupDialog::GetDriverName.md)|Devuelve el controlador utiliza la impresora.|  
|[CPageSetupDialog::GetMargins](../Topic/CPageSetupDialog::GetMargins.md)|Devuelve la configuración de los márgenes actuales de la impresora.|  
|[CPageSetupDialog::GetPaperSize](../Topic/CPageSetupDialog::GetPaperSize.md)|Devuelve el tamaño del papel de impresora.|  
|[CPageSetupDialog::GetPortName](../Topic/CPageSetupDialog::GetPortName.md)|Devuelve el nombre de puerto de salida.|  
|[CPageSetupDialog::OnDrawPage](../Topic/CPageSetupDialog::OnDrawPage.md)|Llamado por el marco para mostrar una imagen de la presentación de una página impresa.|  
|[CPageSetupDialog::PreDrawPage](../Topic/CPageSetupDialog::PreDrawPage.md)|Llamado por el marco antes de mostrar una imagen de la presentación de una página impresa.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPageSetupDialog::m\_psd](../Topic/CPageSetupDialog::m_psd.md)|Una estructura utilizada para personalizar un objeto de `CPageSetupDialog` .|  
  
## Comentarios  
 Esta clase está diseñada para tomar el lugar del cuadro de diálogo configuración de impresión.  
  
 Para utilizar un objeto de `CPageSetupDialog` , primero cree el objeto mediante el constructor de `CPageSetupDialog` .  Una vez que se ha construido el cuadro de diálogo, puede establecer o modificar cualquier valor del miembro de datos de `m_psd` para inicializar los valores de los controles del cuadro de diálogo.  La estructura de [m\_psd](../Topic/CPageSetupDialog::m_psd.md) es de **PAGESETUPDLG**escrito.  
  
 Después de inicializar los controles de cuadro de diálogo, llame a la función miembro de `DoModal` para mostrar el cuadro de diálogo y permitir al usuario a las opciones de impresión seleccionadas.  `DoModal` devuelve si el usuario ha seleccionado del botón ACEPTAR \(**IDOK**\) o delete \(**IDCANCEL**\).  
  
 Si `DoModal` devuelve **IDOK**, puede utilizar algunas de las funciones miembro de entity\_CODECPageSetupDialog, o tenga acceso al miembro de datos de `m_psd` , para recuperar entrada de información del usuario.  
  
> [!NOTE]
>  Después de que se descarta el cuadro de diálogo de OLE Page Setup de común, ningún cambio realizado por el usuario no se guardarán en el marco.  Depende de la propia aplicación para guardar cualquier valor de este cuadro de diálogo en una ubicación permanente, como miembro de la aplicación o de clase de aplicación.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 `CPageSetupDialog`  
  
## Requisitos  
 **encabezado:** afxdlgs.h  
  
## Vea también  
 [ejemplo WORDPAD de MFC](../../top/visual-cpp-samples.md)   
 [CCommonDialog Class](../../mfc/reference/ccommondialog-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)