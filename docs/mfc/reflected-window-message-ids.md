---
title: "Identificadores de mensaje de ventana reflejada | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "OCM_CTLCOLORBTN"
  - "OCM_PARENTNOTIFY"
  - "OCM_VKEYTOITEM"
  - "OCM_CTLCOLORSTATIC"
  - "OCM_HSCROLL"
  - "OCM_CHARTOITEM"
  - "OCM_DRAWITEM"
  - "OCM_MEASUREITEM"
  - "OCM_COMPAREITEM"
  - "OCM_COMMAND"
  - "OCM_NOTIFY"
  - "OCM_CTLCOLORMSGBOX"
  - "OCM_DELETEITEM"
  - "OCM_CTLCOLORLISTBOX"
  - "OCM_CTLCOLORDLG"
  - "OCM_CTLCOLOREDIT"
  - "OCM_CTLCOLORSCROLLBAR"
  - "OCM_VSCROLL"
  - "OCM_CTLCOLOR"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "mensajes, reflejados"
  - "OCM_ (mensajes)"
  - "OCM_CHARTOITEM (mensaje)"
  - "OCM_COMMAND (mensaje)"
  - "OCM_COMPAREITEM (mensaje)"
  - "OCM_CTLCOLOR (mensaje)"
  - "OCM_CTLCOLORBTN (mensaje)"
  - "OCM_CTLCOLORDLG (mensaje)"
  - "OCM_CTLCOLOREDIT (mensaje)"
  - "OCM_CTLCOLORLISTBOX (mensaje)"
  - "OCM_CTLCOLORMSGBOX (mensaje)"
  - "OCM_CTLCOLORSCROLLBAR (mensaje)"
  - "OCM_CTLCOLORSTATIC (mensaje)"
  - "OCM_DELETEITEM (mensaje)"
  - "OCM_DRAWITEM (mensaje)"
  - "OCM_HSCROLL (mensaje)"
  - "OCM_MEASUREITEM (mensaje)"
  - "OCM_NOTIFY (mensaje)"
  - "OCM_PARENTNOTIFY (mensaje)"
  - "OCM_VKEYTOITEM (mensaje)"
  - "OCM_VSCROLL (mensaje)"
  - "mensajes reflejados"
  - "mensajes reflejados, identificadores de mensaje de ventana"
ms.assetid: 3417ff51-ff9f-458c-bff4-17c200f00d96
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Identificadores de mensaje de ventana reflejada
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La forma rápida de crear un control ActiveX, u otro control especializado, es crear subclases de una ventana.  Para obtener más información, vea [Controles ActiveX de MFC: Crear subclases de un Control de Windows](../mfc/mfc-activex-controls-subclassing-a-windows-control.md).  
  
 Para evitar que el contenedor del control reciba los mensajes de la ventana enviados por un control derivado de Windows, [COleControl](../mfc/reference/colecontrol-class.md) crea una ventana de “reflector” para interceptar determinados mensajes de la ventana y enviarlos al control.  El control, en el procedimiento de la ventana, puede procesar estos mensajes reflejados con acciones adecuados para un control ActiveX.  
  
 La tabla siguiente muestra los mensajes se interceptan que los mensajes correspondientes que la ventana reflector envía.  
  
|Mensaje enviado por el control|Mensaje reflejado al control|  
|------------------------------------|----------------------------------|  
|[\<caps:sentence id\="tgt8" sentenceid\="873e43d4b95944ef6a24e5ce86283a86" class\="tgtSentence"\>WM\_COMMAND\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/ms647591)|**OCM\_COMMAND**|  
|[\<caps:sentence id\="tgt10" sentenceid\="4c05f2ab21ae1d3135515bcc85612c15" class\="tgtSentence"\>WM\_CTLCOLORBTN\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/bb761849)|**OCM\_CTLCOLORBTN**|  
|[\<caps:sentence id\="tgt12" sentenceid\="e7bee49a92d5957960a50078a6c4ff10" class\="tgtSentence"\>WM\_CTLCOLOREDIT\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/bb761691)|**OCM\_CTLCOLOREDIT**|  
|[\<caps:sentence id\="tgt14" sentenceid\="4e7d61c9b6e22695496cf799f4174d9f" class\="tgtSentence"\>WM\_CTLCOLORDLG\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/ms645417)|**OCM\_CTLCOLORDLG**|  
|[\<caps:sentence id\="tgt16" sentenceid\="b5346b7e4f669cf080415efd51991c0b" class\="tgtSentence"\>WM\_CTLCOLORLISTBOX\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/bb761360)|**OCM\_CTLCOLORLISTBOX**|  
|[\<caps:sentence id\="tgt18" sentenceid\="f54bf5423a419738db0a4fc1a27e71ff" class\="tgtSentence"\>WM\_CTLCOLORSCROLLBAR\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/bb787573)|**OCM\_CTLCOLORSCROLLBAR**|  
|[\<caps:sentence id\="tgt20" sentenceid\="306fe5385a2d130a1af7eeaae7b7a410" class\="tgtSentence"\>WM\_CTLCOLORSTATIC\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/bb787524)|**OCM\_CTLCOLORSTATIC**|  
|[\<caps:sentence id\="tgt22" sentenceid\="52a902695a63460a61e98eb25c7aaac8" class\="tgtSentence"\>WM\_DRAWITEM\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/bb775923)|**OCM\_DRAWITEM**|  
|[\<caps:sentence id\="tgt24" sentenceid\="1649d347836eae1c6da98a2558f21bca" class\="tgtSentence"\>WM\_MEASUREITEM\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/bb775925)|**OCM\_MEASUREITEM**|  
|[\<caps:sentence id\="tgt26" sentenceid\="b69690f0bfa93c77a0c3077dbe5df0a0" class\="tgtSentence"\>WM\_DELETEITEM\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/bb761362)|**OCM\_DELETEITEM**|  
|[\<caps:sentence id\="tgt28" sentenceid\="dabc6d41d06da731f6ffbd80a7be9c47" class\="tgtSentence"\>WM\_VKEYTOITEM\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/bb761364)|**OCM\_VKEYTOITEM**|  
|[\<caps:sentence id\="tgt30" sentenceid\="bbc462c9e39eb6780c8c68e9bebdcf3f" class\="tgtSentence"\>WM\_CHARTOITEM\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/bb761358)|**OCM\_CHARTOITEM**|  
|[\<caps:sentence id\="tgt32" sentenceid\="a27395293112eab4e984332653a806da" class\="tgtSentence"\>WM\_COMPAREITEM\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/bb775921)|**OCM\_COMPAREITEM**|  
|[\<caps:sentence id\="tgt34" sentenceid\="788353476482225cba177b38a64c12fc" class\="tgtSentence"\>WM\_HSCROLL\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/bb787575)|**OCM\_HSCROLL**|  
|[\<caps:sentence id\="tgt36" sentenceid\="184504e211dd9d704614b4971227c841" class\="tgtSentence"\>WM\_VSCROLL\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/bb787577)|**OCM\_VSCROLL**|  
|[\<caps:sentence id\="tgt38" sentenceid\="5472066e1b7be200d04d419a3a7d9b2e" class\="tgtSentence"\>WM\_PARENTNOTIFY\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/ms632638.aspx)|**OCM\_PARENTNOTIFY**|  
|[\<caps:sentence id\="tgt40" sentenceid\="023ec208a39d8192158a43906a5d18b5" class\="tgtSentence"\>WM\_NOTIFY\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/bb775583)|**OCM\_NOTIFY**|  
  
> [!NOTE]
>  Si el control se ejecuta en un sistema Win32, hay varios tipos de mensajes de **WM\_CTLCOLOR\*** puede recibir.  Para obtener más información, vea **WM\_CTLCOLORBTN**, **WM\_CTLCOLORDLG**, **WM\_CTLCOLOREDIT**, **WM\_CTLCOLORLISTBOX**, **WM\_CTLCOLORMSGBOX**, **WM\_CTLCOLORSCROLLBAR**, **WM\_CTLCOLORSTATIC**.  
  
## Vea también  
 [Controles ActiveX MFC: Creación de subclases de un control de Windows](../mfc/mfc-activex-controls-subclassing-a-windows-control.md)   
 [TN062: Reflexión de mensajes para controles de Windows](../mfc/tn062-message-reflection-for-windows-controls.md)