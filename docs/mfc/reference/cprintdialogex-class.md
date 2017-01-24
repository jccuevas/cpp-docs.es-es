---
title: "CPrintDialogEx Class | Microsoft Docs"
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
  - "CPrintDialogEx"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CPrintDialogEx class"
  - "Imprimir (cuadro de diálogo)"
  - "Print Setup dialog box"
ms.assetid: 1d506703-ee1c-44cc-b4ce-4e778fec26b8
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CPrintDialogEx Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Encapsula los servicios proporcionados por la hoja de propiedades de impresión de Windows 2000.  
  
## Sintaxis  
  
```  
class CPrintDialogEx : public CCommonDialog  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPrintDialogEx::CPrintDialogEx](../Topic/CPrintDialogEx::CPrintDialogEx.md)|Crea un objeto `CPrintDialogEx`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPrintDialogEx::CreatePrinterDC](../Topic/CPrintDialogEx::CreatePrinterDC.md)|Crear un contexto de dispositivo de la impresora sin mostrar el cuadro de diálogo imprimir.|  
|[CPrintDialogEx::DoModal](../Topic/CPrintDialogEx::DoModal.md)|Muestra el cuadro de diálogo y permite que el usuario realice selecciones.|  
|[CPrintDialogEx::GetCopies](../Topic/CPrintDialogEx::GetCopies.md)|recupera el número de copias solicitadas.|  
|[CPrintDialogEx::GetDefaults](../Topic/CPrintDialogEx::GetDefaults.md)|Valores predeterminados del dispositivo de recupera sin mostrar un cuadro de diálogo.|  
|[CPrintDialogEx::GetDeviceName](../Topic/CPrintDialogEx::GetDeviceName.md)|Recupera el nombre actualmente de dispositivo de impresora seleccionada.|  
|[CPrintDialogEx::GetDevMode](../Topic/CPrintDialogEx::GetDevMode.md)|Recupera la estructura de `DEVMODE` .|  
|[CPrintDialogEx::GetDriverName](../Topic/CPrintDialogEx::GetDriverName.md)|Recupera el nombre del controlador de dispositivo de impresión sistema\- definido.|  
|[CPrintDialogEx::GetPortName](../Topic/CPrintDialogEx::GetPortName.md)|Recupera el nombre actualmente del puerto de impresora seleccionada.|  
|[CPrintDialogEx::GetPrinterDC](../Topic/CPrintDialogEx::GetPrinterDC.md)|Recupera un identificador al contexto de dispositivo de impresora.|  
|[CPrintDialogEx::PrintAll](../Topic/CPrintDialogEx::PrintAll.md)|Determina si imprimir todas las páginas del documento.|  
|[CPrintDialogEx::PrintCollate](../Topic/CPrintDialogEx::PrintCollate.md)|Determina si las copias intercaladas se solicitadas.|  
|[CPrintDialogEx::PrintCurrentPage](../Topic/CPrintDialogEx::PrintCurrentPage.md)|Determina si imprimir la página actual del documento.|  
|[CPrintDialogEx::PrintRange](../Topic/CPrintDialogEx::PrintRange.md)|Determina si imprimir sólo un intervalo especificado de páginas.|  
|[CPrintDialogEx::PrintSelection](../Topic/CPrintDialogEx::PrintSelection.md)|Determina si imprimir sólo actualmente los elementos seleccionados.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPrintDialogEx::m\_pdex](../Topic/CPrintDialogEx::m_pdex.md)|Una estructura utilizada para personalizar un objeto de `CPrintDialogEx` .|  
  
## Comentarios  
 Puede utilizar el marco para administrar muchos aspectos del proceso de impresión para la aplicación.  Para obtener más información sobre cómo usar el marco para administrar tareas de impresión, vea el artículo [el imprimir](../../mfc/printing.md).  
  
 Si desea que la aplicación controle la impresión sin la implicación del marco, puede utilizar la clase de `CPrintDialogEx` “tal cual” con el constructor proporcionado, o puede derivar su propia clase de cuadro de diálogo de `CPrintDialogEx` y escribir un constructor para satisfacer sus necesidades.  En cualquier caso, estos cuadros de diálogo se comportarán como cuadros de diálogo estándar de MFC dado que se derivan de la clase `CCommonDialog`.  
  
 Para utilizar un objeto de `CPrintDialogEx` , primero cree el objeto mediante el constructor de `CPrintDialogEx` .  Una vez que se ha construido el cuadro de diálogo, puede establecer o modificar cualquier valor de la estructura de [m\_pdex](../Topic/CPrintDialogEx::m_pdex.md) para inicializar los valores de los controles del cuadro de diálogo.  La estructura de `m_pdex` es de [PRINTDLGEX](http://msdn.microsoft.com/library/windows/desktop/ms646844)escrito.  Para obtener más información sobre esta estructura, vea [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Si no se proporciona sus propios identificadores en `m_pdex` para los miembros de **hDevMode** y de **hDevNames** , asegúrese de llamar a la función de Windows **GlobalFree** para estos identificadores cuando se hace con el cuadro de diálogo.  
  
 Después de inicializar los controles de cuadro de diálogo, llame a la función miembro de `DoModal` para mostrar el cuadro de diálogo y permitir al usuario a las opciones de impresión seleccionadas.  Cuando `DoModal` cambia, puede determinar si el usuario seleccionó OK, aplica, o botón Cancelar.  
  
 Si el usuario presionó ACEPTAR, puede utilizar las funciones miembro de entity\_CODECPrintDialogEx para recuperar la entrada de información del usuario.  
  
 La función miembro de `CPrintDialogEx::GetDefaults` es útil para recuperar los valores predeterminados actuales de la impresora sin mostrar un cuadro de diálogo.  Este método no requiere ninguna interacción con el usuario.  
  
 Puede utilizar la función de Windows **CommDlgExtendedError** para determinar si se ha producido un error durante la inicialización del cuadro de diálogo y para obtener más información sobre el error.  Para obtener más información sobre esta función, vea [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Para obtener más información sobre cómo utilizar `CPrintDialogEx`, vea [Clases comunes de diálogo](../../mfc/common-dialog-classes.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 `IObjectWithSite`  
  
 `IPrintDialogCallback`  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 `CPrintDialogEx`  
  
## Requisitos  
 **encabezado:** afxdlgs.h  
  
## Vea también  
 [CCommonDialog Class](../../mfc/reference/ccommondialog-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CPrintInfo Structure](../../mfc/reference/cprintinfo-structure.md)