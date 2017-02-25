---
title: "Inicializar el cuadro de di&#225;logo | Microsoft Docs"
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
  - "inicializar cuadros de diálogo"
  - "cuadros de diálogo de MFC, inicializar"
  - "cuadros de diálogo modales, inicializar"
  - "cuadros de diálogo no modales, inicializar"
  - "OnInitDialog (método)"
ms.assetid: 968142f5-19f9-4b34-a1d4-8e6412d4379b
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Inicializar el cuadro de di&#225;logo
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una vez creados el cuadro de diálogo y todos sus controles pero justo antes del cuadro de diálogo \(de cualquiera tipo\) en la pantalla, se llama a la función miembro de [OnInitDialog](../Topic/CDialog::OnInitDialog.md) del diálogo.  Para un cuadro de diálogo modal, esto ocurre durante la llamada de `DoModal` .  Para un cuadro de diálogo no modal, se llama a `OnInitDialog` cuando se llama a **crear** .  Normalmente se reemplaza `OnInitDialog` para inicializar los controles del cuadro de diálogo, como establecer el texto inicial de un cuadro de edición.  Se debe llamar a la función miembro de `OnInitDialog` de la clase base, `CDialog`, override de `OnInitDialog` .  
  
 Si desea establecer el color de fondo del cuadro de diálogo \(y el del resto de los cuadros de diálogo en la aplicación\), vea [Establecer el color de fondo del cuadro de diálogo](../mfc/setting-the-dialog-box’s-background-color.md).  
  
## Vea también  
 [Ciclo de vida de un cuadro de diálogo](../mfc/life-cycle-of-a-dialog-box.md)