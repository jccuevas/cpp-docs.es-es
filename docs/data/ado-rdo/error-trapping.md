---
title: "Interceptaci&#243;n de errores | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "controles ActiveX [C++], interceptación de errores"
  - "interceptación de errores [C++]"
ms.assetid: c509b089-a542-44be-8f22-dc5832967a48
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Interceptaci&#243;n de errores
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

En el enlace de datos, la interceptación de errores tiene dos orígenes: los eventos de error y los objetos de error.  
  
##  <a name="vcreferrortrappingviaerrorevents"></a> Interceptación de errores mediante eventos de error  
 Tanto el control de datos ADO como el control RemoteData de RDO tienen eventos de error.  Normalmente, deberá establecer un controlador de eventos.  Los controladores de eventos tienen la siguiente firma:  
  
```  
void CMyDlg::OnErrorAdodc1(long ErrorNumber,  
                           BSTR* FAR Description,  
                           long Scode,  
                           LPCTSTR Source,  
                           LPCTSTR HelpFile,  
                           long HelpContext,  
                           BOOL FAR* fCancelDisplay)  
```  
  
 Normalmente, el campo Description contiene datos, pero los campos ErrorNumber y Scode sólo si se dan errores COM.  Un controlador de eventos estándar debe mostrar el campo Description en un cuadro de mensaje.  Por ejemplo:  
  
```  
{  
   USES_CONVERSION;     
// note: have to include the ATL file ATLConv.h to use the ATL conversion macros  
   ::AfxMessageBox(OLE2T(*Description), MB_OK);  
}  
```  
  
 Sin embargo, el control de datos ADO y el control RemoteData de RDO ya están configurados para interceptar eventos de error, por lo que no es necesario agregar código.  
  
##  <a name="vcreferrortrappingviaerrorobjects"></a> Interceptación de errores mediante objetos de error  
 Tanto ADO como RDO tienen objetos de error.  Al generar [clases contenedoras](../../data/ado-rdo/wrapper-classes.md), el control RemoteData de RDO genera contenedores para los objetos de error; en cambio, el control ADO no los genera.  
  
 El control de datos ADO muestra automáticamente los mensajes de error de ADO.  
  
## Vea también  
 [Enlace de datos con controles ActiveX en Visual C\+\+](../../data/ado-rdo/databinding-with-activex-controls-in-visual-cpp.md)