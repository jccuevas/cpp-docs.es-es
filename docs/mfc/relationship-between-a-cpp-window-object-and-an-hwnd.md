---
title: "Relaci&#243;n entre un objeto Window de C++ y un HWND | Microsoft Docs"
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
  - "HWND"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CWnd (clase), HWND"
  - "HWND"
  - "HWND, Window (objetos)"
  - "Window (objetos) [C++], HWND y"
  - "Windows (ventana) [C++]"
ms.assetid: f2e76340-6691-4ee6-9424-0345634a9469
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Relaci&#243;n entre un objeto Window de C++ y un HWND
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

*El objeto* de ventana es un objeto de clase de C\+\+ `CWnd` \(o una clase derivada\) que el programa crea directamente.  Procede y va en respuesta al constructor del programa y las llamadas del destructor.  *La ventana*de Windows, por otro lado, es un identificador opaco a una estructura de datos interna de Windows que corresponde a una ventana y consume recursos del sistema si existe.  Una ventana de Windows se identifica mediante un “identificador de ventana” \(`HWND`\) y creado después de que el objeto de `CWnd` es creado por una llamada a la función miembro de **crear** de la clase `CWnd`.  La ventana se puede destruir cualquiera por una llamada del programa o por la acción de un usuario.  El identificador de ventana se almacena en la variable miembro de `m_hWnd` de objeto de la ventana.  La ilustración siguiente muestra la relación entre el objeto de la ventana de C\+\+ y la ventana de Windows.  Crear las ventanas se explica en [Crear Windows](../mfc/creating-windows.md).  Destrucción de las ventanas se explica en [Objetos de destrucción de la ventana](../mfc/destroying-window-objects.md).  
  
 ![Objeto de ventana CWnd y ventana resultante](../mfc/media/vc37fj1.png "vc37FJ1")  
Objeto de ventana y ventana de Windows  
  
## Vea también  
 [Window \(Objetos\)](../mfc/window-objects.md)