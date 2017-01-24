---
title: "Using Contained Windows | Microsoft Docs"
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
  - "ATL, ventanas"
  - "contained windows in ATL"
  - "windows [C++], ATL"
ms.assetid: 7b3d79e5-b569-413f-9b98-df4f14efbe2b
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Using Contained Windows
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

ATL implementa las ventanas incluidas con [CContainedWindowT](../atl/reference/ccontainedwindowt-class.md).  Una ventana que representa una ventana que delega sus mensajes a un objeto contenedor en lugar de administrarlos en su propia clase.  
  
> [!NOTE]
>  No necesita derivar una clase de `CContainedWindowT` para utilizar las ventanas incluidas.  
  
 Con las ventanas contenidas, puede crear utiliza una clase existente de Windows o crear subclases de una ventana existente.  Para crear una ventana que utiliza una clase existente de Windows, primero especifique el nombre de clase existente en el constructor del objeto de `CContainedWindowT` .  A continuación llamada `CContainedWindowT::Create`.  Para crear subclases de una ventana existente, no es necesario especificar un nombre de clase de Windows \(paso **NULL** al constructor\).  Llamar al método de `CContainedWindowT::SubclassWindow` con el identificador de la ventana que se subclases.  
  
 Normalmente utiliza las ventanas incluidas como miembros de datos de una clase de contenedor.  el contenedor no necesita ser una ventana; sin embargo, debe derivar de [CMessageMap](../atl/reference/cmessagemap-class.md).  
  
 Una ventana contenida puede utilizar mapas alternativos de mensajes para controlar sus mensajes.  Si tiene más de una ventana contenida, debe declarar varios mapas alternativos de mensajes, cada correspondiente a una ventana contenida independiente.  
  
## Ejemplo  
 A continuación se muestra un ejemplo de una clase contenedora con dos ventanas contenidas:  
  
 [!code-cpp[NVC_ATL_Windowing#67](../atl/codesnippet/CPP/using-contained-windows_1.h)]  
  
 Para obtener más información sobre las ventanas contenidas, vea el ejemplo de [SUBEDIT](../top/visual-cpp-samples.md) .  
  
## Vea también  
 [Clases de ventanas](../atl/atl-window-classes.md)