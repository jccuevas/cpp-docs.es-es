---
title: "CMultiPageDHtmlDialog Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMultiPageDHtmlDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMultiPageDHtmlDialog class"
ms.assetid: 971accc1-824d-4df4-b4c1-b1a20e0f7e4f
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CMultiPageDHtmlDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Un diálogo de varias páginas muestra las páginas HTML varias secuencialmente y administra los eventos de cada página.  
  
## Sintaxis  
  
```  
class CMultiPageDHtmlDialog : public CDHtmlDialog  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMultiPageDHtmlDialog::CMultiPageDHtmlDialog](../Topic/CMultiPageDHtmlDialog::CMultiPageDHtmlDialog.md)|Construye \(asistente\-estilo\) un objeto de varias páginas de diálogo DHTML.|  
|[CMultiPageDHtmlDialog::~CMultiPageDHtmlDialog](../Topic/CMultiPageDHtmlDialog::~CMultiPageDHtmlDialog.md)|Destruye un objeto de varias páginas de diálogo DHTML.|  
  
## Comentarios  
 el mecanismo para hacer el es [Mapa de eventos DHTML y dirección URL](http://msdn.microsoft.com/es-es/2a7332f0-79d7-46e4-b816-0a618c46777a), que contiene [mapas incrustados de eventos](../Topic/BEGIN_EMBED_DHTML_EVENT_MAP.md) para cada página.  
  
## Ejemplo  
 Este diálogo de varias páginas supone a tres recursos HTML que definen simple asistente\-como funcionalidad.  la primera página tiene un botón de `Next` , el segundo un botón de **anterior** y de `Next` , y el tercero un botón de **anterior** .  Cuando uno de los botones se presiona, la función [CDHtmlDialog:: LoadFromResource](../Topic/CDHtmlDialog::LoadFromResource.md) de un controlador para cargar la nueva página apropiada.  
  
 las partes pertinentes de la declaración de clase \(en CMyMultiPageDlg.h\):  
  
 [!code-cpp[NVC_MFCDocView#181](../../mfc/codesnippet/CPP/cmultipagedhtmldialog-class_1.h)]  
  
 Las partes pertinentes de implementación de la clase \(en CMyMultipageDlg.cpp\):  
  
 [!code-cpp[NVC_MFCDocView#182](../../mfc/codesnippet/CPP/cmultipagedhtmldialog-class_2.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDHtmlSinkHandlerBase2`  
  
 `CDHtmlSinkHandlerBase1`  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CDHtmlSinkHandler`  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CDHtmlEventSink`  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)  
  
 `CMultiPageDHtmlDialog`  
  
## Requisitos  
 **encabezado:** afxdhtml.h  
  
## Vea también  
 [CDHtmlDialog Class](../../mfc/reference/cdhtmldialog-class.md)   
 [Multipage DHTML and URL Event Maps \(NIB\)](http://msdn.microsoft.com/es-es/2a7332f0-79d7-46e4-b816-0a618c46777a)