---
title: "Registrar clases de ventana | Microsoft Docs"
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
  - "WndProc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AfxRegisterWndClass (método)"
  - "clases [C++], registrar clases de ventana"
  - "MFC, ventanas"
  - "registrar clases de ventana"
  - "Registro, registrar clases"
  - "clases de ventana, registrar"
  - "WinMain (método)"
  - "WinMain (método), y registrar clases de ventana"
  - "WndProc (método)"
ms.assetid: 30994bc4-a362-43da-bcc5-1bf67a3fc929
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Registrar clases de ventana
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La ventana “clases” en la programación tradicional para Windows define las características de una “clase” \(no clase de c\+\+.\) del que cualquier número de ventanas se puedan crear.  Este tipo de clase es una plantilla o un modelo para crear ventanas.  
  
## Registro de la clase de ventana en programas de Tradicional para Windows  
 En un programa tradicional para Windows, sin MFC, se procesa todos los mensajes a una ventana en su “procedimiento de ventana” o “**WndProc**.” **WndProc** se asocia a una ventana mediante “un proceso del registro de la clase de ventana”.  La ventana principal se registra en la función de `WinMain` , pero otras clases de ventanas se pueden registrar en cualquier lugar de la aplicación.  El registro depende de una estructura que contiene un puntero a la función de **WndProc** junto con las especificaciones de cursor, pincel de fondo, etc.  La estructura se pasa como parámetro, junto con el nombre de cadena de clase, en una llamada anterior a la función de **RegisterClass** .  Así, una clase de registro pueden compartirse entre varias ventanas.  
  
## Registro de la clase de ventana en programas MFC  
 En cambio, la mayoría de actividad del registro de la clase de ventana se hace automáticamente en un programa de base de MFC.  Si utiliza MFC, se deriva normalmente la clase de ventana de c\+\+. de una clase existente de biblioteca utilizando la sintaxis normal de C\+\+ para la herencia de la clase.  El marco sigue usando “clases tradicionales de registro”, y proporciona varias estándar, registrado automáticamente cuando es necesario.  Puede registrar clases adicionales de registro llamando a [Clase](../Topic/AfxRegisterWndClass.md) función global y después pasa la clase registrada a la función miembro de **crear** de `CWnd`.  Como se describe aquí, “clase tradicional del registro” en Windows no debe confundirse con la clase en cuestión.  
  
 Para obtener más información, vea [Nota técnica 1](../mfc/tn001-window-class-registration.md).  
  
## Vea también  
 [Crear ventanas](../mfc/creating-windows.md)