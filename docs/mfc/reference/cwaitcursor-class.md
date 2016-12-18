---
title: "CWaitCursor Class | Microsoft Docs"
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
  - "CWaitCursor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cursores, wait cursor"
  - "CWaitCursor class"
  - "wait cursors"
ms.assetid: 5dfae2ff-d7b6-4383-b0ad-91e0868c67b3
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CWaitCursor Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona una manera de una línea de mostrar una espera el cursor, que se muestra normalmente como reloj de arena, mientras se está realizando una operación larga.  
  
## Sintaxis  
  
```  
class CWaitCursor  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CWaitCursor::CWaitCursor](../Topic/CWaitCursor::CWaitCursor.md)|Construye un objeto de `CWaitCursor` y muestra el cursor de espera.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CWaitCursor::Restore](../Topic/CWaitCursor::Restore.md)|Restablece el cursor de espera después de cambiar.|  
  
## Comentarios  
 `CWaitCursor` no tiene una clase base.  
  
 Buen Windows que programa prácticas requiere que se muestra una espera el cursor cada vez que realice una operación que mantenga un tiempo considerable.  
  
 Para mostrar una espera el cursor, simplemente defina una variable de `CWaitCursor` antes de que el código que realiza la operación larga.  El constructor del objeto provoca automáticamente el cursor de espera que se muestre.  
  
 Cuando el objeto salga del ámbito \(al final del bloque en el que se declara el objeto de `CWaitCursor` \), su destructor establece el cursor al cursor anterior.  Es decir el objeto realiza la limpieza necesaria automáticamente.  
  
> [!NOTE]
>  Debido a cómo funcionan los constructores y destructores, los objetos de `CWaitCursor` se declaran siempre como variables locales — los nunca declaran como variables globales ni se asignaron con **nuevo**.  
  
 Si realiza una operación que podría producir el cursor que se cambiará, como mostrar un cuadro de mensaje o un cuadro de diálogo, llame a la función miembro de [Restaurar](../Topic/CWaitCursor::Restore.md) para restaurar el cursor de espera.  Es aceptable llamar a **Restaurar** incluso cuando una espera el cursor se muestra actualmente.  
  
 Otra manera de mostrar una espera el cursor es utilizar la combinación de [CCmdTarget::BeginWaitCursor](../Topic/CCmdTarget::BeginWaitCursor.md), de [CCmdTarget::EndWaitCursor](../Topic/CCmdTarget::EndWaitCursor.md), y quizás de [CCmdTarget::RestoreWaitCursor](../Topic/CCmdTarget::RestoreWaitCursor.md).  Sin embargo, `CWaitCursor` es más fácil utilizar porque no es necesario establecer el cursor al cursor anterior cuando se hace con la operación larga.  
  
> [!NOTE]
>  MFC establece y restaura el cursor mediante la función virtual de [CWinApp::DoWaitCursor](../Topic/CWinApp::DoWaitCursor.md) .  Puede reemplazar esta función para proporcionar un comportamiento personalizado.  
  
## Jerarquía de herencia  
 `CWaitCursor`  
  
## Requisitos  
 **Encabezado:** afxwin.h  
  
## Ejemplo  
 [!code-cpp[NVC_MFCWindowing#62](../../mfc/reference/codesnippet/CPP/cwaitcursor-class_1.cpp)]  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CCmdTarget::BeginWaitCursor](../Topic/CCmdTarget::BeginWaitCursor.md)   
 [CCmdTarget::EndWaitCursor](../Topic/CCmdTarget::EndWaitCursor.md)   
 [CCmdTarget::RestoreWaitCursor](../Topic/CCmdTarget::RestoreWaitCursor.md)   
 [CWinApp::DoWaitCursor](../Topic/CWinApp::DoWaitCursor.md)   
 [Cómo se hago: ¿Cambie el Cursor en una aplicación de la clase de windows presentation foundation Microsoft?](http://go.microsoft.com/fwlink/?LinkID=128044)