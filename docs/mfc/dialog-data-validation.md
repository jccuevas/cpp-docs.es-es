---
title: "Validaci&#243;n de datos de cuadro de di&#225;logo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "validación de datos [C++], cuadros de diálogo"
  - "validación de datos [C++], cuadros de mensaje"
  - "DDV (validación de datos de cuadro de diálogo) [C++]"
  - "cuadros de diálogo [C++], validar datos"
  - "validar datos [C++], entrada de datos del cuadro de diálogo"
  - "validar datos [C++], cuadros de mensaje"
ms.assetid: f070c309-2044-4ff2-8c92-1ec1ea84af58
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Validaci&#243;n de datos de cuadro de di&#225;logo
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Puede especificar la validación además de intercambio de datos llamando a funciones de DDV, como se muestra en el ejemplo de [Diálogo de intercambio de datos](../mfc/dialog-data-exchange.md).  La llamada de `DDV_MaxChars` en el ejemplo valida que la cadena especificada en el control de cuadro de texto no está más de 20 caracteres.  La función de DDV alerta normalmente al usuario un cuadro de mensaje si se produce un error en la validación y coloca el foco en el control que provoca para que el usuario puede repetir los datos.  Una función de DDV de un control determinado debe llamar inmediatamente después de que la función de DDX para el mismo controla.  
  
 También puede definir dispone custom DDX y rutinas de DDV.  Para obtener información sobre estos y otros aspectos de DDX y de DDV, vea [Nota técnica 26 de MFC](../mfc/tn026-ddx-and-ddv-routines.md).  
  
 [Asistente para agregar variables miembro](../ide/add-member-variable-wizard.md) escribirá todas las llamadas de DDX y de DDV en el mapa de datos.  
  
## Vea también  
 [Intercambio y validación de datos de cuadros de diálogo](../mfc/dialog-data-exchange-and-validation.md)   
 [Ciclo de vida de un cuadro de diálogo](../mfc/life-cycle-of-a-dialog-box.md)   
 [Intercambio de datos de cuadro de diálogo](../mfc/dialog-data-exchange.md)