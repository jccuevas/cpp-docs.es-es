---
title: "Contenedores de controles ActiveX: Insertar un control en una aplicaci&#243;n de contenedor de controles | Microsoft Docs"
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
  - "contenedores de controles ActiveX [C++], insertar controles"
  - "controles ActiveX [C++], agregar a proyectos"
ms.assetid: bbb617ff-872f-43d8-b4d6-c49adb16b148
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Contenedores de controles ActiveX: Insertar un control en una aplicaci&#243;n de contenedor de controles
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Antes de poder tener acceso a un control ActiveX de aplicación contenedora de controles ActiveX, debe agregar el control ActiveX a la aplicación contenedora mediante el cuadro de diálogo [Insertar control ActiveX](../mfc/insert-activex-control-dialog-box.md) .  
  
 Para agregar un control ActiveX al proyecto de contenedor de controles ActiveX, vea [Controles ActiveX de vista y a un cuadro de diálogo](../mfc/viewing-and-adding-activex-controls-to-a-dialog-box.md).  
  
 Una vez que agregue el control, necesita agregar una variable miembro \(del control ActiveX escribe\) en la clase del cuadro de diálogo.  Para obtener más información sobre este procedimiento, vea [Agregar una variable miembro](../ide/adding-a-member-variable-visual-cpp.md).  
  
 Una vez que ha agregado a la variable miembro una clase, denominada una clase contenedora, automáticamente se genera y se agrega al proyecto.  Se utiliza esta clase como una interfaz entre el contenedor del control y el control incrustado.  
  
## Vea también  
 [Contenedores de controles ActiveX](../mfc/activex-control-containers.md)