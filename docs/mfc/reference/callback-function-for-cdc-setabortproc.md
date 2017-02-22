---
title: "Funci&#243;n de devoluci&#243;n de llamada para CDC::SetAbortProc | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Callback Function for CDC::SetAbortProc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "funciones de devolución de llamada, for CDC::SetAbortProc"
ms.assetid: daa36d5d-15de-40fc-8d37-a865d06c4710
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# Funci&#243;n de devoluci&#243;n de llamada para CDC::SetAbortProc
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El nombre *AbortFunc* es un marcador de posición para el nombre de función aplicación\- proporcionado.  
  
## Sintaxis  
  
```  
  
      BOOL CALLBACK EXPORT AbortFunc(   
   HDC hPr,   
   int code    
);  
```  
  
#### Parámetros  
 *hPr*  
 Identifica el contexto del dispositivo.  
  
 `code`  
 Especifica si se ha producido un error.  Es 0 si se ha producido ningún error.  Es **SP\_OUTOFDISK** si el administrador de impresión está actualmente espacio en disco insuficiente y más espacio en disco disponible si la aplicación espera.  Si `code` es **SP\_OUTOFDISK**, la aplicación no tiene que anular el trabajo de impresión.  Si no lo hace, debe hacer que el administrador de impresión llamando a la función de **PeekMessage** o de **GetMessage** Windows.  
  
## Valor devuelto  
 El valor devuelto de la función de aborto\- controlador es distinto de cero si el trabajo de impresión es continuar, y 0 si se cancela.  
  
## Comentarios  
 El nombre real se debe exportar como se describe en la sección notas de [CDC::SetAbortProc](../Topic/CDC::SetAbortProc.md).  
  
## Requisitos  
 **Encabezado:** afxwin.h  
  
## Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDC::SetAbortProc](../Topic/CDC::SetAbortProc.md)