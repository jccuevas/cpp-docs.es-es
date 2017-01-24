---
title: "Funciones de devoluci&#243;n de llamada usadas por MFC | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.functions"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "funciones de devolución de llamada"
  - "funciones de devolución de llamada, MFC"
  - "funciones [C++], devolución de llamada"
  - "MFC, funciones de devolución de llamada"
ms.assetid: b2a6857c-fdd3-45ec-8fd8-2e71fac77582
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Funciones de devoluci&#243;n de llamada usadas por MFC
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Tres funciones de devolución de llamada aparecen en la biblioteca Microsoft Foundation Class.  Descripción de las funciones de devolución de llamada que se pasan a [CDC::EnumObjects](../Topic/CDC::EnumObjects.md), de [CDC::GrayString](../Topic/CDC::GrayString.md), y de [CDC::SetAbortProc](../Topic/CDC::SetAbortProc.md) después de este tema.  Para uso general de las funciones de devolución de llamada, vea la sección comentarios de estas funciones miembro.  Observe que todas las funciones de devolución de llamada deben excepciones de MFC catch antes de volver a Windows, dado que las excepciones no se pueden producir entre límites de devolución de llamada.  Para obtener más información sobre excepciones, vea el artículo [Excepciones](../../mfc/exception-handling-in-mfc.md).  
  
## Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)