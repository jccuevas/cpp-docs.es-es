---
title: "CDataExchange Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDataExchange"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDataExchange class"
  - "DDV (dialog data validation)"
  - "DDV (dialog data validation), custom DDV routines"
  - "DDX (intercambio de datos de cuadros de diálogo)"
  - "DDX (intercambio de datos de cuadros de diálogo), between dialog and CDialog"
  - "DDX (intercambio de datos de cuadros de diálogo), custom DDX routines"
  - "DDX (intercambio de datos de cuadros de diálogo), direction of exchange"
  - "DDX/DDV"
  - "DDX/DDV, CDataExchange class"
  - "DDX/DDV, Technical Note 26"
  - "exchanging data between dialogs and CDialogs"
  - "m_bSaveAndValidate"
  - "validar datos, dialog box data entry"
ms.assetid: 84ed6113-325d-493e-a75d-223f03a992b8
caps.latest.revision: 20
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDataExchange Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Admite el diálogo rutinas de validación de datos de intercambio y \(DDV\) de diálogo utilizadas por las clases base de Microsoft.  
  
## Sintaxis  
  
```  
class CDataExchange  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDataExchange::CDataExchange](../Topic/CDataExchange::CDataExchange.md)|Crea un objeto `CDataExchange`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDataExchange::Fail](../Topic/CDataExchange::Fail.md)|Se invoca cuando se produce un error en la validación.  Se reinicia el foco en el control anterior y producen una excepción.|  
|[CDataExchange::PrepareCtrl](../Topic/CDataExchange::PrepareCtrl.md)|Prepara el control especificado para el intercambio de datos o validación.  Uso de los controles de nonedit.|  
|[CDataExchange::PrepareEditCtrl](../Topic/CDataExchange::PrepareEditCtrl.md)|Prepara el control de edición especificado para el intercambio de datos o validación.|  
|[CDataExchange::PrepareOleCtrl](../Topic/CDataExchange::PrepareOleCtrl.md)|Prepara el control OLE especificado para el intercambio de datos o validación.  Uso de los controles de nonedit.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDataExchange::m\_bSaveAndValidate](../Topic/CDataExchange::m_bSaveAndValidate.md)|Marca para la dirección de DDX y de DDV.|  
|[CDataExchange::m\_pDlgWnd](../Topic/CDataExchange::m_pDlgWnd.md)|El cuadro de diálogo o la ventana donde tiene lugar el intercambio de datos.|  
  
## Comentarios  
 `CDataExchange` no tiene una clase base.  
  
 Utilice esta clase si escribe las rutinas de intercambio de datos para los tipos de datos personalizados o controles, o si es escribir poseer rutinas de validación de datos.  Para obtener más información sobre cómo escribir poseer las rutinas de DDX y de DDV, vea [nota técnica 26](../../mfc/tn026-ddx-and-ddv-routines.md).  Para obtener información general sobre DDX y de DDV, vea [diálogo Data Exchange y validación](../../mfc/dialog-data-exchange-and-validation.md) y [cuadros de diálogo](../../mfc/dialog-boxes.md).  
  
 Un objeto de `CDataExchange` proporciona información de contexto necesaria para que DDX y DDV ocurran.  El marcador `m_bSaveAndValidate` es **FALSO** cuando DDX se utiliza para rellenar los valores iniciales de los controles de cuadro de diálogo de los miembros de datos.  El marcador `m_bSaveAndValidate` es **TRUE** cuando DDX se utiliza para establecer los valores actuales de los controles de cuadro de diálogo en los miembros de datos y cuando DDV se utiliza para validar los valores de datos.  Si se produce un error en la validación de DDV, el procedimiento de DDV mostrará un cuadro de mensaje que explica el error de entrada.  El procedimiento de DDV llamará a **Error** para restaurar el foco al control que provoca y para producir una excepción para detener el proceso de validación.  
  
## Jerarquía de herencia  
 `CDataExchange`  
  
## Requisitos  
 **Encabezado:** afxwin.h  
  
## Vea también  
 [ejemplo VIEWEX de MFC](../../top/visual-cpp-samples.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CWnd::DoDataExchange](../Topic/CWnd::DoDataExchange.md)   
 [CWnd::UpdateData](../Topic/CWnd::UpdateData.md)