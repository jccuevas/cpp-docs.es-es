---
title: "CPaintDC Class | Microsoft Docs"
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
  - "CPaintDC"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CPaintDC class"
  - "OnPaint handler"
  - "WM_PAINT message"
ms.assetid: 7e245baa-bf9b-403e-a637-7218adf28fab
caps.latest.revision: 22
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CPaintDC Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Una clase de dispositivo\-contexto derivada de [CDC](../../mfc/reference/cdc-class.md).  
  
## Sintaxis  
  
```  
class CPaintDC : public CDC  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPaintDC::CPaintDC](../Topic/CPaintDC::CPaintDC.md)|Construye `CPaintDC` conectado a [CWnd](../../mfc/reference/cwnd-class.md)especificado.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPaintDC::m\_ps](../Topic/CPaintDC::m_ps.md)|contiene [PAINTSTRUCT](../../mfc/reference/paintstruct-structure.md) utilizado para pintar el área cliente.|  
  
### Miembros de datos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPaintDC::m\_hWnd](../Topic/CPaintDC::m_hWnd.md)|`HWND` a las que está asociado este objeto de `CPaintDC` .|  
  
## Comentarios  
 Realiza [CWnd:: BeginPaint](../Topic/CWnd::BeginPaint.md) en tiempo de construcción y [CWnd:: EndPaint](../Topic/CWnd::EndPaint.md) en tiempo de destrucción.  
  
 Un objeto de `CPaintDC` solo se puede usar al responder a un mensaje de [WM\_PAINT](http://msdn.microsoft.com/library/windows/desktop/dd145213) , normalmente en la función miembro de controlador de mensajes `OnPaint` .  
  
 Para obtener más información sobre cómo utilizar `CPaintDC`, vea [Contextos de dispositivo](../../mfc/device-contexts.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CDC](../../mfc/reference/cdc-class.md)  
  
 `CPaintDC`  
  
## Requisitos  
 **Encabezado:** afxwin.h  
  
## Vea también  
 [ejemplo MDI de MFC](../../top/visual-cpp-samples.md)   
 [CDC \(clase\)](../../mfc/reference/cdc-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)