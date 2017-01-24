---
title: "CPrintDialog Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CPrintDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CPrintDialog class"
  - "Imprimir (cuadro de diálogo)"
  - "Print Setup dialog box"
ms.assetid: 5bdb2424-adf8-433d-a97c-df11a83bc4e4
caps.latest.revision: 23
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CPrintDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

encapsula los servicios proporcionados por el cuadro de diálogo común de Windows para imprimir.  
  
## Sintaxis  
  
```  
class CPrintDialog : public CCommonDialog  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPrintDialog::CPrintDialog](../Topic/CPrintDialog::CPrintDialog.md)|Crea un objeto `CPrintDialog`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPrintDialog::CreatePrinterDC](../Topic/CPrintDialog::CreatePrinterDC.md)|Crear un contexto de dispositivo de la impresora sin mostrar el cuadro de diálogo imprimir.|  
|[CPrintDialog::DoModal](../Topic/CPrintDialog::DoModal.md)|Muestra el cuadro de diálogo y permite que el usuario realice una selección.|  
|[CPrintDialog::GetCopies](../Topic/CPrintDialog::GetCopies.md)|recupera el número de copias solicitadas.|  
|[CPrintDialog::GetDefaults](../Topic/CPrintDialog::GetDefaults.md)|Valores predeterminados del dispositivo de recupera sin mostrar un cuadro de diálogo.|  
|[CPrintDialog::GetDeviceName](../Topic/CPrintDialog::GetDeviceName.md)|Recupera el nombre actualmente de dispositivo de impresora seleccionada.|  
|[CPrintDialog::GetDevMode](../Topic/CPrintDialog::GetDevMode.md)|Recupera la estructura de `DEVMODE` .|  
|[CPrintDialog::GetDriverName](../Topic/CPrintDialog::GetDriverName.md)|Recupera el nombre actualmente del controlador de impresora seleccionada.|  
|[CPrintDialog::GetFromPage](../Topic/CPrintDialog::GetFromPage.md)|Recupera la página inicial del intervalo de impresión.|  
|[CPrintDialog::GetPortName](../Topic/CPrintDialog::GetPortName.md)|Recupera el nombre actualmente del puerto de impresora seleccionada.|  
|[CPrintDialog::GetPrinterDC](../Topic/CPrintDialog::GetPrinterDC.md)|Recupera un identificador al contexto de dispositivo de impresora.|  
|[CPrintDialog::GetToPage](../Topic/CPrintDialog::GetToPage.md)|Recupera la página del final del intervalo de impresión.|  
|[CPrintDialog::PrintAll](../Topic/CPrintDialog::PrintAll.md)|Determina si imprimir todas las páginas del documento.|  
|[CPrintDialog::PrintCollate](../Topic/CPrintDialog::PrintCollate.md)|Determina si las copias intercaladas se solicitadas.|  
|[CPrintDialog::PrintRange](../Topic/CPrintDialog::PrintRange.md)|Determina si imprimir sólo un intervalo especificado de páginas.|  
|[CPrintDialog::PrintSelection](../Topic/CPrintDialog::PrintSelection.md)|Determina si imprimir sólo actualmente los elementos seleccionados.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPrintDialog::m\_pd](../Topic/CPrintDialog::m_pd.md)|Una estructura utilizada para personalizar un objeto de `CPrintDialog` .|  
  
## Comentarios  
 Los cuadros de diálogo comunes de impresión proporcionan una manera fácil de implementar los cuadros de diálogo de impresión y configuración de impresión de una manera coherente con las normas de Windows.  
  
> [!NOTE]
>  La clase de `CPrintDialogEx` encapsula los servicios proporcionados por la hoja de propiedades de impresión de Windows 2000.  Para obtener más información vea información general de [CPrintDialogEx](../../mfc/reference/cprintdialogex-class.md) .  
  
 La funcionalidad de entity\_CODECPrintDialog se reemplaza por la de [CPageSetupDialog](../../mfc/reference/cpagesetupdialog-class.md), diseñada para proporcionarle con un cuadro de diálogo común para la instalación y la configuración de página de impresión.  
  
 Puede utilizar el marco para administrar muchos aspectos del proceso de impresión para la aplicación.  En este caso, el marco muestra automáticamente el cuadro de diálogo común de Windows para imprimir.  También puede tener la impresión del identificador del marco para la aplicación pero reemplazar el cuadro de diálogo común de impresión con su propio cuadro de diálogo de impresión.  Para obtener más información sobre cómo usar el marco para administrar tareas de impresión, vea el artículo [el imprimir](../../mfc/printing.md).  
  
 Si desea que la aplicación controle la impresión sin la implicación del marco, puede utilizar la clase de `CPrintDialog` “tal cual” con el constructor proporcionado, o puede derivar su propia clase de cuadro de diálogo de `CPrintDialog` y escribir un constructor para satisfacer sus necesidades.  En cualquier caso, estos cuadros de diálogo se comportarán como cuadros de diálogo estándar de MFC dado que se derivan de la clase `CCommonDialog`.  
  
 Para utilizar un objeto de `CPrintDialog` , primero cree el objeto mediante el constructor de `CPrintDialog` .  Una vez que se ha construido el cuadro de diálogo, puede establecer o modificar cualquier valor de la estructura de [m\_pd](../Topic/CPrintDialog::m_pd.md) para inicializar los valores de los controles del cuadro de diálogo.  La estructura de `m_pd` es de [PRINTDLG](http://msdn.microsoft.com/library/windows/desktop/ms646843)escrito.  Para obtener más información sobre esta estructura, vea [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Si no se proporciona sus propios identificadores en `m_pd` para los miembros de **hDevMode** y de **hDevNames** , asegúrese de llamar a la función de Windows **GlobalFree** para estos identificadores cuando se hace con el cuadro de diálogo.  Al utilizar la implementación de la configuración de impresión de marco proporcionada por `CWinApp::OnFilePrintSetup`, no es necesario liberar estos identificadores.  Los identificadores atiende `CWinApp` y liberados en el destructor de entity\_CODECWinApp.  Solo es necesario liberar estos identificadores al utilizar `CPrintDialog` independiente.  
  
 Después de inicializar los controles de cuadro de diálogo, llame a la función miembro de `DoModal` para mostrar el cuadro de diálogo y permitir al usuario a las opciones de impresión seleccionadas.  `DoModal` devuelve si el usuario ha seleccionado del botón ACEPTAR \(**IDOK**\) o delete \(**IDCANCEL**\).  
  
 Si `DoModal` devuelve **IDOK**, puede utilizar una de las funciones miembro de entity\_CODECPrintDialog para recuperar la entrada de información del usuario.  
  
 La función miembro de `CPrintDialog::GetDefaults` es útil para recuperar los valores predeterminados actuales de la impresora sin mostrar un cuadro de diálogo.  Esta función miembro no requiere ninguna interacción con el usuario.  
  
 Puede utilizar la función de Windows **CommDlgExtendedError** para determinar si se ha producido un error durante la inicialización del cuadro de diálogo y para obtener más información sobre el error.  Para obtener más información sobre esta función, vea [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 `CPrintDialog` se basa en el archivo de COMMDLG.DLL que envía con las versiones de Windows 3,1 y versiones posteriores.  
  
 Para personalizar el cuadro de diálogo, derive una clase de `CPrintDialog`, proporcionar una plantilla personalizada del cuadro de diálogo, y agregar un mapa de mensajes para procesar mensajes de notificación de controles extendidos.  Cualquier mensaje sin procesar se debe pasar en la clase base.  Personalizar la función de enlace no es necesario.  
  
 Para procesar el mismo mensaje de manera diferente dependiendo de si el cuadro de diálogo es imprimir o configuración de impresión, debe derivar una clase para cada cuadro de diálogo.  También debe reemplazar la función de Windows **AttachOnSetup** , que controla la creación de un nuevo cuadro de diálogo cuando el botón de la configuración de impresión se selecciona dentro de un cuadro de diálogo imprimir.  
  
 Para obtener más información sobre cómo utilizar `CPrintDialog`, vea [Clases comunes de diálogo](../../mfc/common-dialog-classes.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 `CPrintDialog`  
  
## Requisitos  
 **encabezado:** afxdlgs.h  
  
## Vea también  
 [ejemplo DIBLOOK de MFC](../../top/visual-cpp-samples.md)   
 [CCommonDialog Class](../../mfc/reference/ccommondialog-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CPrintInfo Structure](../../mfc/reference/cprintinfo-structure.md)