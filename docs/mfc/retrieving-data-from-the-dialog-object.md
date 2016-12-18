---
title: "Recuperar datos del objeto de cuadro de di&#225;logo | Microsoft Docs"
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
  - "capturar la entrada del usuario"
  - "datos [MFC], cuadros de diálogo"
  - "datos [MFC], recuperar"
  - "recuperación de datos [C++], cuadros de diálogo"
  - "DDX (intercambio de datos de cuadros de diálogo) [C++]"
  - "DDX (intercambio de datos de cuadros de diálogo) [C++], acerca de DDX"
  - "DDX (intercambio de datos de cuadros de diálogo) [C++], recuperar datos del objeto de cuadro de diálogo"
  - "controles de cuadro de diálogo [C++], inicializar valores"
  - "datos del cuadro de diálogo [C++]"
  - "datos del cuadro de diálogo [C++], recuperar"
  - "cuadros de diálogo [C++], recuperar datos de usuario"
  - "GetDlgItemText (método)"
  - "GetWindowText (método)"
  - "cuadros de diálogo de MFC, recuperar los datos proporcionados por el usuario"
  - "recuperar datos"
  - "SetDlgItemText (método)"
  - "SetWindowText (método)"
  - "datos proporcionados por el usuario [C++], recuperar de los cuadros de diálogo de MFC"
ms.assetid: bdca2b61-6b53-4c2e-b426-8712c7a38ec0
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Recuperar datos del objeto de cuadro de di&#225;logo
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El marco de trabajo proporciona una manera fácil de inicializar los valores de los controles en un cuadro de diálogo y recuperar valores de los controles.  El enfoque manual más laborioso es llamar a funciones como las funciones miembro de `SetDlgItemText` y de `GetDlgItemText` de la clase `CWnd`, que se aplican a las ventanas de control.  Con estas funciones, tiene acceso a cada control individualmente para establecer u obtener su valor, llamadas a funciones como `SetWindowText` y `GetWindowText`.  El enfoque de marco automatiza la inicialización y la recuperación.  
  
 El diálogo intercambio de datos \(DDX\) permite intercambiar datos entre los controles del cuadro de diálogo y variables miembros en el objeto de diálogo más fácilmente.  Este intercambio funciona ambas formas.  Para inicializar los controles en el cuadro de diálogo, puede establecer los valores de miembros de datos del objeto de cuadro de diálogo, y el marco transferirá los valores a los controles antes de que se muestre el cuadro de diálogo.  A continuación puede actualizar en cualquier momento a los miembros de datos de cuadro de diálogo con los datos especificados por el usuario.  En ese momento, puede utilizar los datos haciendo referencia a las variables miembro de datos.  
  
 También puede organizar los valores de los controles de cuadro de diálogo que se va a validar automáticamente con la validación de datos \(DDV\) de diálogo.  
  
 DDX y DDV se explican con más detalle en [Diálogo Data Exchange y validación](../mfc/dialog-data-exchange-and-validation.md).  
  
 Para un cuadro de diálogo modal, puede recuperar los datos que escribió el usuario cuando `DoModal` devuelve **IDOK** pero antes de que se destruye el objeto cuadro de diálogo.  Para un cuadro de diálogo no modal, puede recuperar datos de objeto del diálogo en cualquier momento llamando a `UpdateData` con el argumento **VERDADERO** y después tener acceso a las variables miembro de la clase de diálogo.  Este tema se explica con más detalle en [Diálogo Data Exchange y validación](../mfc/dialog-data-exchange-and-validation.md).  
  
## Vea también  
 [Ciclo de vida de un cuadro de diálogo](../mfc/life-cycle-of-a-dialog-box.md)